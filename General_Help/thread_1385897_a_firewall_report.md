---
title: "a firewall report"
date: 2010-01-20
forum: General Help
---

### Post by gerontium on 2010-01-20
[SIZE=4][FONT=Book Antiqua]I Don't often have problems that manuals of various kinds can't solve. But. There's always a first time.
After a Brief period using the dreaded vista on a dell inspiron 1750, I switched to ubuntu, it being the only linux distro that appreciated the wireless hardware
was pleasantly surprised to discover ubuntu has improved a thousand fold since I last used it, release 1 or 2, way back, my current version appears to be 9 something and is probably out of date already if the speed of linux development hasn't changed much in the last 10 years.

All these years and would you believe, No-one ever tried to hack my linux installations?

My Windows Installations were always targets, but that is no surprise.

My surprise was that some hack attempts have been reported by my firewall - (Firestarter) - (the best I've had), 

There isn't a problem, but, I wonder if someone could develop a program for ubuntu that would allow you to report such events in as much detail as the firewall can give to someone out there who would do something about it? Or at least find a way of contacting where the attack is launched from and asking "please? Bill gates Doesn't live here! Desist!"

Time:Jan 17 20:16:23 Direction: Unknown In:eth2 Out: Port:49701 Source:208.110.170.18 Destination:192.168.0.2 Length:1420 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 20:19:32 Direction: Unknown In:eth2 Out: Port:17573 Source:77.201.121.184 Destination:192.168.0.2 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 20:19:32 Direction: Unknown In:eth2 Out: Port:17573 Source:77.201.121.184 Destination:192.168.0.2 Length:47 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan 17 20:19:35 Direction: Unknown In:eth2 Out: Port:17573 Source:77.201.121.184 Destination:192.168.0.2 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 20:22:21 Direction: Unknown In:eth2 Out: Port:8080 Source:125.224.194.161 Destination:192.168.0.2 Length:48 TOS:0x00 Protocol:TCP Service:Http-alt
Time:Jan 17 20:28:23 Direction: Unknown In:eth2 Out: Port:6881 Source:94.120.181.15 Destination:192.168.0.2 Length:48 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 17 20:33:07 Direction: Unknown In:eth2 Out: Port:6881 Source:88.232.228.196 Destination:192.168.0.2 Length:93 TOS:0x00 Protocol:UDP Service:BitTorrent
Time:Jan 17 20:46:09 Direction: Unknown In:eth2 Out: Port:2967 Source:211.144.92.176 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 21:07:45 Direction: Unknown In:eth2 Out: Port:6881 Source:79.159.117.244 Destination:192.168.0.2 Length:52 TOS:0x00 Protocol:TCP Service:BitTorrent
Time:Jan 17 21:13:14 Direction: Unknown In:eth2 Out: Port:53 Source:192.168.0.1 Destination:192.168.0.2 Length:79 TOS:0x00 Protocol:ICMP Service:DNS
Time:Jan 17 21:36:01 Direction: Unknown In:eth2 Out: Port:2967 Source:218.240.32.166 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 22:02:40 Direction: Unknown In:eth2 Out: Port:5900 Source:81.98.21.142 Destination:192.168.0.2 Length:64 TOS:0x00 Protocol:TCP Service:VNC
Time:Jan 17 22:02:42 Direction: Unknown In:eth2 Out: Port:2967 Source:60.173.11.12 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 22:02:43 Direction: Unknown In:eth2 Out: Port:5900 Source:81.98.21.142 Destination:192.168.0.2 Length:64 TOS:0x00 Protocol:TCP Service:VNC
Time:Jan 17 22:10:17 Direction: Unknown In:eth2 Out: Port:22 Source:202.117.51.250 Destination:192.168.0.2 Length:48 TOS:0x00 Protocol:TCP Service:SSH
Time:Jan 17 22:16:27 Direction: Unknown In:eth2 Out: Port:8080 Source:125.224.196.21 Destination:192.168.0.2 Length:48 TOS:0x00 Protocol:TCP Service:Http-alt
Time:Jan 17 22:44:18 Direction: Unknown In:eth2 Out: Port:1434 Source:219.149.53.239 Destination:192.168.0.2 Length:404 TOS:0x00 Protocol:UDP Service:Ms-sql-m
Time:Jan 17 23:16:45 Direction: Unknown In:eth2 Out: Port:3128 Source:222.136.98.98 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 23:16:45 Direction: Unknown In:eth2 Out: Port:8080 Source:222.136.98.98 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Http-alt
Time:Jan 17 23:16:45 Direction: Unknown In:eth2 Out: Port:9090 Source:222.136.98.98 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan 17 23:16:45 Direction: Unknown In:eth2 Out: Port:1080 Source:222.136.98.98 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Socks
Time:Jan 17 23:26:43 Direction: Unknown In:eth2 Out: Port:1433 Source:221.5.251.170 Destination:192.168.0.2 Length:44 TOS:0x00 Protocol:TCP Service:Ms-sql-s

Time:Jan 19 12:56:52 Direction: Unknown In:eth2 Out: Port:23 Source:85.96.61.226 Destination:192.168.0.2 Length:60 TOS:0x00 Protocol:TCP Service:Telnet

Time:Jan 20 07:35:38 Direction: Unknown In:eth2 Out: Port: Source:85.96.61.226 Destination:192.168.0.2 Length:1028 TOS:0x00 Protocol:ICMP Service:Unknown
Time:Jan 20 07:41:00 Direction: Unknown In:eth2 Out: Port:64472 Source:202.148.192.2 Destination:192.168.0.2 Length:48 TOS:0x00 Protocol:UDP Service:Unknown
Time:Jan 20 07:50:29 Direction: Unknown In:eth2 Out: Port:48353 Source:118.120.79.185 Destination:192.168.0.2 Length:81 TOS:0x00 Protocol:UDP Service:Unknown

85.96.61.226 - dsl.dynamic859661226.ttnet.net.tr
221.5.251.170
222.136.98.98 - hn.kd.ny.adsl
219.149.53.239
125.224.196.21 - 125-224-196-21.dynamic.hinet.net
202.117.51.250 - hpc.xjtu.edu.cn
81.98.21.142 - client-81-98-21-142.cht-bng-013.adsl.virginmedia.net
60.173.11.12
218.240.32.166 
192.168.0.1 - icmp only(info incorrect - 192.168.0.1 is a default router dns ip allocation) - (our home router has this ip address, the only way this could have been used is as a security breech) but why icmp?
79.159.117.244 - 244.Red-79-159-117.staticIP.rima-tde.net
211.144.92.176 - reserve.cableplus.com.cn
88.232.228.196
94.120.181.15
125.224.194.184 - 125-224-194-161.dynamic.hinet.net
77.201.121.184 - 184.121.201.77.rev.gaoland.net
208.110.170.18 - pdfdownload.org
202.148.192.2 - abs-cn-2.192.148.202.aircel.co.in
118.120.79.185

If any other ubuntu user notices these addresses, who do we report them to?

And can Wine be affected by anything that is sneaky enough to get through?
[/FONT][/SIZE]

---

### Post by dvlchd3 on 2010-01-20
First of all, I have found Firstarter reports A LOT of false positives!  Frankly, I've never had much luck understanding their log files.  Secondly, attacks are inevitable.  There is no way to be 100% secure, and anyone who ever makes this claim is just the next target.  Linux is much more secure than other operating systems because of its accomplishments with very few LOC (lines of code) as well as its multi-user environment.  Debian also has made great steps in security by taking the close all ports unless an application needs them open approach to firewall scripts.

Thirdly, the software you are inquiring about does exist.  However, it is typically only used for servers as it takes resources that most desktop users would want to utilize.  However, if you feel less resources out weighs the benefits of monitoring your computer, install Snort.  ([http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472))

Finally, a much more secure firewall will always help.  The below script will make you essentially invisible on the network.  It will not respond to ping requests, and will make port and stealth scans take a long time!  The only way to see your computer is if the potential attacker is monitoring network activity, or runs stealth scans on your entire network.  The only thing this script allows into the machine are responses to connection you created, or connections related to a connection you created.  For most users, this will not impact anything.

This script is meant to be placed in executed from /etc/network/if-up.d/firewall

To install it, type:
```

gksudo gedit /etc/network/if-up.d/firewall

```

Copy and paste the following code into the gedit window:
```

#!/bin/bash

########################################################
# Copyright (C) 2009 Dan Buhrman
#
# Permission to use, copy, modify and distribute this software
# and its documentation for educational, research, private and
# non-profit purposes, without fee, and without a written
# agreement is hereby granted. This software is provided as an
# example and basis for individual firewall development. This
# software is provided without warranty.
#
# Any material furnished by Dan Buhrman is furnished on an
# "as is" basis. He makes not warranties of any kind, either
# expressed or implied as to any matter including, but not
# limited to, warranty of fitness for a particular purpose,
# exclusivity or results obtained from use of the material.
########################################################

# Remove any existing rules from all chains
iptables --flush
iptables -t nat --flush
iptables -t mangle --flush

# Set the default filter table policy
iptables --policy INPUT DROP
iptables --policy OUTPUT ACCEPT
iptables --policy FORWARD DROP

#Remove any pre-existing user-defined chains
iptables --delete-chain
iptables -t nat --delete-chain
iptables -t mangle --delete-chain

# Unlimited traffic on the loopback interface
iptables -A INPUT -i lo -j ACCEPT

#Using Connection State to By-pass Rule Checking
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Network Ghouls
# Deny access to jerks
# /etc/rd.d/rd.firewall.blocked contains a list of
# iptables -A INPUT -s address -j DROP
# rules to block any access.

# Refuse any connection from problem sites
if [ -f /etc/rc.d/rc.firewall.blocked ]; then
. /etc/rc.d/rc.firewall.blocked
fi

```

Change the permissions on the file
```

sudo chmod 700 /etc/network/if-up.d/firewall

```

Now the script will start after your network interface comes up.  To start the script manually, simply type:
```

sudo /etc/network/if-up.d/firewall

```

All Done  :)

---

### Post by gerontium on 2010-01-20
Thankyou, I didn't know about the firewall script, and have applied it, a nice piece of code by the way.
Unfortunately as for false positives, I live near an airport, which can't be helped but nmap scans have generated some extremely complex traceroute data on the five serious attempts recorded, The only other place I have seen traceroutes like that was in evidence of botnets, and as some of the protocols appeared to be related to a windows sql worm, I figured that the original network sources of the attempts/attacks is infected and the users themselves may be unaware of what their computers are doing.?

For now I will pass on the resource heavy Snort, and see how the script you gave me worked out
thanks again :)

---

### Post by Kevbert on 2010-01-20
Thanks for the scripts dvlchd3, I'll install them now.
You want 'sudo' to start the firewall script manually.

---

### Post by dvlchd3 on 2010-01-25
Thanks for that, it should be corrected now.

---

