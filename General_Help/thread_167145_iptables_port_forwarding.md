---
title: "iptables port forwarding"
date: 2006-04-27
forum: General Help
---

### Post by chocolatetoothpaste on 2006-04-27
Hey all, I am having trouble getting port forwarding going on my firewall.  I want incoming connections on port 8007 to be directed to machine 192.168.1.7.  Plain and simply, it doesn't work.  I connected my machine directly to my dsl modem, and it forwards just fine.  But when I try and run it through my firewall, no dice.  So if anyone has experience with iptables, please help.  Here are my firewall rules:
```

# Path to executables
IPTABLES=/usr/sbin/iptables
MODPROBE=/sbin/modprobe

OUT_DEV=eth0    # Internet
INT_DEV=eth1    # Internal/protected network.

# Stop forwarding while setting up.
echo "0" > /proc/sys/net/ipv4/ip_forward

# Uncomment the following line to enable logging:
# LOGGING="yes"

# Uncomment & set the next three vars to activate the BScap captive portal.
#BSCAP="yes"
# set to your DNS server IP's: (for BScap)
#DNSHOSTS="192.168.1.254 192.168.9.254"
# set to your private IP range: (for BScap)
#CAPNET="192.168.1.0/24"

# Optional Modules:
${MODPROBE} ip_conntrack_ftp
${MODPROBE} ip_nat_ftp
${MODPROBE} ip_conntrack_irc
${MODPROBE} ip_nat_irc
#${MODPROBE} ip_owner
${MODPROBE} ipt_state

# Only needed if we're going to log.
[ -n "$LOGGING" ] && ${MODPROBE} ipt_LOG

if [ -n "$BSCAP" ]; then
        ${MODPROBE} ipt_mac
        ${MODPROBE} ipt_mark
        ${MODPROBE} ipt_REDIRECT
fi

# Flush tables & setup Policy
${IPTABLES} -F  # flush chains
${IPTABLES} -X  # delete user chains
${IPTABLES} -Z  # zero counters
for t in `cat /proc/net/ip_tables_names`
do
        ${IPTABLES} -F -t $t
        ${IPTABLES} -X -t $t
        ${IPTABLES} -Z -t $t
done

### BEGIN IPTABLES rules ###

${IPTABLES} -P INPUT DROP       # Policy = DROP
${IPTABLES} -P OUTPUT DROP      #  Drop all packets that are
${IPTABLES} -P FORWARD DROP     #  not specifically accepted.

# make interactive sesions a bit more interactive under load
${IPTABLES} -t mangle -N SETTOS
${IPTABLES} -A SETTOS -t mangle -p TCP --sport ssh -j TOS --set-tos Minimize-Delay
${IPTABLES} -A SETTOS -t mangle -p TCP --sport ftp -j TOS --set-tos Minimize-Delay
${IPTABLES} -A SETTOS -t mangle -p TCP --sport ftp-data -j TOS --set-tos Maximize-Throughput

# Local interface - do not delete!
${IPTABLES} -A INPUT -i lo -j ACCEPT
${IPTABLES} -A OUTPUT -o lo -j ACCEPT

# We accept anything from the inside.
${IPTABLES} -A INPUT -i ${INT_DEV} -j ACCEPT
${IPTABLES} -A OUTPUT -o ${INT_DEV} -j ACCEPT

# Allow our firewall to connect.
${IPTABLES} -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
${IPTABLES} -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# Allow Ping and friends.
${IPTABLES} -A INPUT  -p icmp -i ${OUT_DEV} -j DROP
${IPTABLES} -A INPUT  -p icmp -j ACCEPT
${IPTABLES} -A OUTPUT -p icmp -j ACCEPT

# Fast reject for Ident to eliminate email delays.
${IPTABLES} -A INPUT -p TCP --dport 113 -i ${OUT_DEV} -j REJECT --reject-with tcp-reset

# Uncomment/modify the next 4 lines to forward a service to an internal IP.
SERVER_IP=192.168.1.7   # Internal IP of server.
PORT=8007               # 22 = SSH.  Change to 80 for web server, etc.
${IPTABLES} -A PREROUTING -i ${OUT_DEV} -t nat -p TCP --dport $PORT -j DNAT --to ${SERVER_IP}:${PORT}
${IPTABLES} -A FORWARD -p TCP -d ${SERVER_IP} --dport $PORT -i ${OUT_DEV} -o ${INT_DEV} -j ACCEPT

# Uncomment/modify the next 2 lines to open a port on the internet to Devil Linux.
# PORT=25               # 25 = SMTP.  Change to the port you wish to open.
# ${IPTABLES} -A INPUT -p tcp --dport $PORT -i ${OUT_DEV} -j ACCEPT

${IPTABLES} -t mangle -A PREROUTING -j SETTOS

if [ -n "$BSCAP" ]; then
        # Uncomment chmod if BScap is diskless and htdocs is under /root
        # chmod a+x /root
        # Block outgoing port 25 to prevent spam from being sent
        [ -n "$LOGGING" ] && \
          ${IPTABLES} -A FORWARD -p tcp --dport 25 -i ${OUT_DEV} -j LOG --log-prefix "Outgoing email: "
        ${IPTABLES} -A FORWARD -p tcp --dport 25 -i ${OUT_DEV} -j REJECT
        # Open up 443 (https) for BScap admin connections from the outside.
        # Add a "-s" to limit the connections to a specific network or IP.
        ${IPTABLES} -A INPUT -p tcp --dport 443 -i ${OUT_DEV} -j ACCEPT
        # Open up 22 (SSH) for remote DL administration
        # Add a "-s" to limit the connections to a specific network or IP.
        ${IPTABLES} -A INPUT -p tcp --dport 22 -i ${OUT_DEV} -j ACCEPT
        # Chain for BScap rules (manipulated externally with PHP)
        ${IPTABLES} -t mangle -N BScap
        ${IPTABLES} -t mangle -A PREROUTING -i ${INT_DEV} -j MARK --set-mark 0x4        ${IPTABLES} -t mangle -A PREROUTING -j BScap
        # Redirect all unauthenticated Internet access to local web server
        ${IPTABLES} -t nat -A PREROUTING -p tcp -m mark --mark 0x4 --dport 80 -j REDIRECT --to-ports 80
        ${IPTABLES} -t nat -A PREROUTING -p tcp -m mark --mark 0x4 --dport 443 -j REDIRECT --to-ports 443
        # Always allow DNS lookups
        for h in $DNSHOSTS
        do
                ${IPTABLES} -t nat -A POSTROUTING -s ${CAPNET} -d $h -p tcp --dport 53 -j MASQUERADE
                ${IPTABLES} -t nat -A POSTROUTING -s ${CAPNET} -d $h -p udp --dport 53 -j MASQUERADE
        done
        # Allow only BScap authenticated IP/MAC combo's access to Internet (Masquerading)
        ${IPTABLES} -t nat -A POSTROUTING -o ${OUT_DEV} -m mark --mark 0x2 -j MASQUERADE
else
        # Masquerading for everyone (aka NAT, PAT, ...)
        ${IPTABLES} -t nat -A POSTROUTING -o ${OUT_DEV} -j MASQUERADE
fi

# Block invalid connections from the internet.
[ -n "$LOGGING" ] && \
  ${IPTABLES} -A FORWARD -m state --state NEW,INVALID -i ${OUT_DEV} -j LOG --log-prefix "FORWARD INVALID: "
${IPTABLES} -A FORWARD -m state --state NEW,INVALID -i ${OUT_DEV} -j DROP

# Allow connections to the internet from the internal network.
${IPTABLES} -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
${IPTABLES} -A FORWARD -m state --state NEW -i ${INT_DEV} -j ACCEPT

# Prevent NetBIOS and Samba from leaking.
${IPTABLES} -t nat -A PREROUTING -p TCP --dport 135 -j DROP
${IPTABLES} -t nat -A PREROUTING -p UDP --dport 135 -j DROP
${IPTABLES} -t nat -A PREROUTING -p TCP --dport 137:139 -j DROP
${IPTABLES} -t nat -A PREROUTING -p UDP --dport 137:139 -j DROP
${IPTABLES} -t nat -A PREROUTING -p TCP --dport 445 -j DROP
${IPTABLES} -t nat -A PREROUTING -p UDP --dport 445 -j DROP

# Log invalid packets from DROP policy:
if [ -n "$LOGGING" ] ; then
    ${IPTABLES} -A INPUT -d 255.255.255.255 -j DROP # do not log broadcasts
    ${IPTABLES} -A INPUT -d 224.0.0.0/8 -j DROP # do not log Microsoft multicasts
    ${IPTABLES} -A INPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-prefix "INPUT policy: "
    ${IPTABLES} -A OUTPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-prefix "OUTPUT policy: "
    ${IPTABLES} -A FORWARD -m limit --limit 3/minute --limit-burst 3 -j LOG --log-prefix "FORWARD policy: "
fi

### END IPTABLES rules ###

# enable dynamic IP address following
echo 2 > /proc/sys/net/ipv4/ip_dynaddr

# stop some smurf attacks.
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

# Don't accept source routed packets.
echo "0" > /proc/sys/net/ipv4/conf/all/accept_source_route

# Syncookies
echo "1" > /proc/sys/net/ipv4/tcp_syncookies

# Stop IP spoofing,
for interface in /proc/sys/net/ipv4/conf/*/rp_filter; do
        echo "1" > $interface
done

# Stop ICMP redirect
for interface in /proc/sys/net/ipv4/conf/*/accept_redirects; do
        echo "0" > ${interface}
done

# Enable bad error message protection.
echo "1" > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses

# Enabling IP forwarding.
echo "1" > /proc/sys/net/ipv4/ip_forward

``` 
PS - and just so no one thinks otherwise, I have googled this to death and can't find anything that works.
PPS - If you can think of anything else that I should check on to see if it is blocking my connections, I am all ears.  I am not positive the script is the problem, it is just my first assumption.
The firewall is a very stripped down machine.

---

### Post by chocolatetoothpaste on 2006-04-27
bump!

---

### Post by syadnom on 2008-03-04
bump bump bump! good doesnt seem to know the answer to this!

---

### Post by sizzlefire on 2008-03-26
The reason is because a router is a firewall, so therefore you have to configure your firewall to allow connections on that port. Just google instructions on this for your router, and good luck.

---

### Post by wormser on 2008-03-27
> **sizzlefire said:**
> The reason is because a router is a firewall, so therefore you have to configure your firewall to allow connections on that port. Just google instructions on this for your router, and good luck.

Sizzlefire is right. Go here: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by syadnom on 2008-03-27
You must have your firewall also be the default gateway on the target machine, if not, the ACK will be sent to the gateway, which will look like the port forwarding is not working.  the solution is that you need to set up some NAT so that your firewall rewrites the senders address to its address.  that way your target machine will reply to the local machine(because the gw will keep local addresses local) and then the firewall will rewite that address again on the way out.


Internet Host 
12.13.14.15 
->
Firewall inet side (inet 209.210.211.212, lan 192.168.0.10)
209.210.211.212
NAT 12.13.14.15=192.168.0.10
->
Internal Host

reply

Internal Host
->
default gateway(assume 192.168.0.1, requestion 192.168.0.10)
->
gateway keeps the local addresses local and sends it to 192.168.0.10
->
firewall NATs 192.168.0.10=12.13.14.15
WORKS!

I would suggest that you install shorewall instead of trying to manually manipulate iptables.  you get a much nicer solution in shorewall.  also, if you install webmin, it has a very nice shorewall module.

---

