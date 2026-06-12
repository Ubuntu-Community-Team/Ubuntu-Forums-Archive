---
title: "Startup script fails to load"
date: 2011-08-27
forum: General Help
---

### Post by azzid on 2011-08-27
I have a script on my firewall to load rules and policys into iptables.
It is based on a article from Linux Journal by Mick Bauer.

I have changed it from being run by the new startup features in Ubuntu to good old symlinks in rc?.d, but it still will not run.

I think this looks OK:
```

**$ for i in `sudo find /etc | grep iptables_custom | sort | xargs`; do ls -l $i; done** 
-rwxr--r-- 1 root root 8644 2011-08-27 17:40 /etc/init.d/iptables_custom
lrwxrwxrwx 1 root root   25 2011-08-27 17:00 /etc/rc0.d/K20iptables_custom -> ../init.d/iptables_custom
lrwxrwxrwx 1 root root   25 2011-08-27 17:00 /etc/rc1.d/K20iptables_custom -> ../init.d/iptables_custom
lrwxrwxrwx 1 root root   25 2011-08-27 17:00 /etc/rc2.d/S80iptables_custom -> ../init.d/iptables_custom
lrwxrwxrwx 1 root root   25 2011-08-27 17:00 /etc/rc3.d/S80iptables_custom -> ../init.d/iptables_custom
lrwxrwxrwx 1 root root   25 2011-08-27 17:00 /etc/rc4.d/S80iptables_custom -> ../init.d/iptables_custom
lrwxrwxrwx 1 root root   25 2011-08-27 17:00 /etc/rc5.d/S80iptables_custom -> ../init.d/iptables_custom
lrwxrwxrwx 1 root root   25 2011-08-27 17:00 /etc/rc6.d/K20iptables_custom -> ../init.d/iptables_custom

```

But if I reboot the machine it does not load the script.

If I run the script manually it loads all the iptables rules.

The script:
```
#!/bin/bash

### BEGIN INIT INFO
# Provides:		iptables_custom
# Required-Start:	$networking
# Required-Stop:
# Default-Start:
# Default-Stop:		0 6
# Short-Description: Custom bridged iptables rules
### END INIT INFO

#eth0 = WAN
#eth1 = LAN
#eth2 = DMZ

#PATH=/sbin:/bin:/usr/bin
IPTABLES=/sbin/iptables
BRIDGE=br0
LOCALIP=`ifconfig $BRIDGE | head -2 | tail -1 | awk '{ print $2 }' | awk -F : '{ print $2 }'`
LOCALBCAST=`ifconfig $BRIDGE | head -2 | tail -1 | awk '{ print $3 }' | awk -F : '{ print $2 }'`

#. /lib/lsb/init-functions

function valid_ip 
{
    local  ip=$1
    local  stat=1

    if [[ $ip =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}$ ]]; then
        OIFS=$IFS
        IFS='.'
        ip=($ip)
        IFS=$OIFS
        [[ ${ip[0]} -le 255 && ${ip[1]} -le 255 \
            && ${ip[2]} -le 255 && ${ip[3]} -le 255 ]]
        stat=$?
    fi
    return $stat
}

function do_start 
{
	if ! valid_ip $LOCALIP; then echo "False local IP: QUITTING"; exit 3; fi
	if ! valid_ip $LOCALBCAST; then echo "False local broadcast IP: QUITTING"; exit 3; fi

	echo "Loading custom bridged iptables rules"

	# Flush active rules, custom tables
	$IPTABLES --flush
	$IPTABLES --delete-chain
	
	# Set default-deny policies for all three default tables
	$IPTABLES -P INPUT DROP
	$IPTABLES -P FORWARD DROP
	$IPTABLES -P OUTPUT DROP

	# allow ESTABLISHED connections to live
	$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
	$IPTABLES -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
	$IPTABLES -A OUTPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT

	# Allow ping
	$IPTABLES -A INPUT  -p ICMP -j ACCEPT
	$IPTABLES -A OUTPUT -p ICMP -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 -p ICMP -j ACCEPT
	
	# Don't restrict loopback (local process intercommunication)
	$IPTABLES -A INPUT  -i lo -j ACCEPT	
	$IPTABLES -A OUTPUT -o lo -j ACCEPT	

	# Block attempts at spoofed loopback traffic
	$IPTABLES -A INPUT -s $LOCALIP -j DROP

	# pass DHCP queries and responses
	$IPTABLES -A FORWARD -p udp --sport 68 --dport 67 -j ACCEPT
	$IPTABLES -A FORWARD -p udp --sport 67 --dport 68 -j ACCEPT
	$IPTABLES -A INPUT   -p udp --sport 68 --dport 67 -j ACCEPT
	$IPTABLES -A INPUT   -p udp --sport 67 --dport 68 -j ACCEPT
	$IPTABLES -A OUTPUT  -p udp --sport 68 --dport 67 -j ACCEPT
	$IPTABLES -A OUTPUT  -p udp --sport 67 --dport 68 -j ACCEPT

	# let certain hardware into LAN
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 -j ACCEPT # Allow anything from LAN
	$IPTABLES -A FORWARD -m physdev --physdev-out eth1 -m mac --mac-source 01:01:01:01:01:01 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-out eth1 -m mac --mac-source 02:02:02:02:02:02 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-out eth1 -m mac --mac-source 03:03:03:03:03:03 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-out eth1 -m mac --mac-source 04:04:04:04:04:04 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-out eth1 -m mac --mac-source 05:05:05:05:05:05 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-out eth1 -m mac --mac-source 06:06:06:06:06:06 -j ACCEPT 

	# let eth2 out, but block it from eth1
	$IPTABLES -A FORWARD -m physdev --physdev-in eth2 --physdev-out eth1 -j DROP
	$IPTABLES -A FORWARD -m physdev --physdev-in eth2 --physdev-out eth0 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 --physdev-out eth2 -j ACCEPT

	# Allow SSH to firewall
	$IPTABLES -A INPUT -p tcp --dport 22 -j ACCEPT

        # Port knocking to allow ssh to inside interface
	KNOCK1=1111
	KNOCK2=2222
	KNOCK3=3333
	KNOCK4=4444
	$IPTABLES -A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -p tcp --dport $KNOCK1 -m recent --name 1-1-1 --set
	$IPTABLES -N 1-1-IN-2
	$IPTABLES -A 1-1-IN-2 -m recent --name 1-1-1 --remove
	$IPTABLES -A 1-1-IN-2 -m recent --name 1-1-2 --set
	$IPTABLES -A 1-1-IN-2 -j LOG --log-prefix NAME-1-1-IN-2
	$IPTABLES -A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -p tcp --dport $KNOCK1 -m recent --rcheck --name 1-1-1 -j 1-1-IN-2
	$IPTABLES -N 1-1-IN-3
	$IPTABLES -A 1-1-IN-3 -m recent --name 1-1-2 --remove
	$IPTABLES -A 1-1-IN-3 -m recent --name 1-1-3 --set
	$IPTABLES -A 1-1-IN-3 -j LOG --log-prefix NAME-1-1-IN-3
	$IPTABLES -A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -p tcp --dport $KNOCK2 -m recent --rcheck --name 1-1-2 -j 1-1-IN-3
	$IPTABLES -N 1-1-IN-4
	$IPTABLES -A 1-1-IN-4 -m recent --name 1-1-3 --remove
	$IPTABLES -A 1-1-IN-4 -m recent --name 1-1-4 --set
	$IPTABLES -A 1-1-IN-4 -j LOG --log-prefix NAME-1-1-IN-4
	$IPTABLES -A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -p tcp --dport $KNOCK3 -m recent --rcheck --name 1-1-3 -j 1-1-IN-4
	$IPTABLES -N 1-1-IN-5
	$IPTABLES -A 1-1-IN-5 -m recent --name 1-1-4 --remove
	$IPTABLES -A 1-1-IN-5 -m recent --name 1-1-5 --set
	$IPTABLES -A 1-1-IN-5 -j LOG --log-prefix NAME-1-1-IN-5
	$IPTABLES -A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -p tcp --dport $KNOCK4 -m recent --rcheck --name 1-1-4 -j 1-1-IN-5
	$IPTABLES -A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -p tcp --dport 22 -m recent --seconds 5 --rcheck --name 1-1-5 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-in eth0 --physdev-out eth1 -p tcp --dport 5900 -m recent --seconds 5 --rcheck --name 1-1-5 -j ACCEPT
        # End of port knocking to allow ssh to inside interface

	# Allow SSH out
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 -p tcp --dport 22 -j ACCEPT

	# pass DNS queries and their replies
	$IPTABLES -A FORWARD -m physdev --physdev-out eth0 -p udp --dport 53 -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-out eth0 -p tcp --dport 53 -j ACCEPT 
	$IPTABLES -A OUTPUT  -p tcp --dport 53 -j ACCEPT
	$IPTABLES -A OUTPUT  -p udp --dport 53 -j ACCEPT

	# allow http(s)
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -p tcp --dport 80  -j ACCEPT
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -p tcp --dport 443 -j ACCEPT
	$IPTABLES -A OUTPUT  -p tcp --dport 80  -j ACCEPT
	$IPTABLES -A OUTPUT  -p tcp --dport 443 -j ACCEPT

	# allow spotify
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -p tcp --dport 4070 -j ACCEPT

	# allow MSN
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -p tcp --dport 1863 -j ACCEPT
	
	# allow irc
	$IPTABLES -A FORWARD -m physdev --physdev-in eth1 --physdev-out eth0 -p tcp --dport 6667  -j ACCEPT

	# handle BROADCAST
	$IPTABLES -A FORWARD -d $LOCALBCAST     -j DROP
	$IPTABLES -A FORWARD -d 255.255.255.255 -j DROP
	$IPTABLES -A INPUT   -d $LOCALBCAST     -j DROP
	$IPTABLES -A INPUT   -d 255.255.255.255 -j DROP
	# handle multicast
	$IPTABLES -A FORWARD -d 224.0.0.251     -j DROP
	$IPTABLES -A FORWARD -d 239.255.255.250 -j DROP
	$IPTABLES -A FORWARD -d 224.0.0.22      -j DROP

	# cleanup-rules (logging turned off to save disk space and I/O)
#	$IPTABLES -A INPUT -j LOG --log-prefix "Dropped by default (INPUT):"
	$IPTABLES -A INPUT -j DROP
#	$IPTABLES -A OUTPUT -j LOG --log-prefix "Dropped by default (OUTPUT):"
	$IPTABLES -A OUTPUT -j DROP
#	$IPTABLES -A FORWARD -j LOG --log-prefix "Dropped by default (FORWARD):"
	$IPTABLES -A FORWARD -j DROP

}

function do_unload 
{
	$IPTABLES --flush
	$IPTABLES -P INPUT ACCEPT
	$IPTABLES -P OUTPUT ACCEPT
	$IPTABLES -P FORWARD ACCEPT
}

case "$1" in
	start)
		do_start
		;;
	restart|reload|force-reload)
		echo "Reloading bridging iptables rules"
		do_unload
		do_start
		;;
	stop)
		echo "DANGER: Unloading firewall's Packet Filters!"
		do_unload
		;;
	*)
		echo "Usage: $0 start|stop|restart" >&2
		exit 3
		;;
esac
exit 0
```

Can someone please help me troubleshoot this?

---

### Post by dino99 on 2011-08-27
some examples:

[http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown](http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown)

---

### Post by WyleECoyote on 2011-08-27
try copying your script to "/etc/network/if-up.d" and edit the "/etc/network/interfaces" file to load the script it should run it after your network interface is up

[http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html](http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html)

---

### Post by azzid on 2011-08-28
> **WyleECoyote said:**
> try copying your script to "/etc/network/if-up.d" and edit the "/etc/network/interfaces" file to load the script it should run it after your network interface is up

[http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html](http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html)

Worked like a charm!

Removed the script from init.d and rc?.d and added the following to my /etc/network/interfaces:
```
	post-up /etc/network/iptables_custom start
	pre-down /etc/network/iptables_custom stop

```

Now the machine boots with proper iptables rules loaded. :popcorn:

Still confuses me that the previous setup didn't work though...

---

### Post by WyleECoyote on 2011-08-28
glad it worked, and thank you for posting a reply it annoys me when OP does not reply. I think the problem with the init.d etc.. is that it was loading before the net connected and your script does look for active connection, you can either re-write the script and loop it till it connects then continue on or just use the simple fix I posted which takes much less effort on the comp and if for some reason your net does not connect it is not running unneeded in the background.

---

