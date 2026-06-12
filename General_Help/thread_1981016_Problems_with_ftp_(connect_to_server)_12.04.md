---
title: "Problems with ftp (connect to server) 12.04"
date: 2012-05-16
forum: General Help
---

### Post by captainKrash on 2012-05-16
Hi There,

I have recently upgraded from 10.04  to 12.04 and am gradually finding my way around, however I have hit a few snags.

I mainly use SSH to connect to client machines, however, a few only supply ftp credentials. I normally use the 'Connect to server' dialogue to connect to and browse the remote file system. However since upgrading I am unable to get an ftp connection completely.

I  used[ this thread]("http://ubuntuforums.org/showthread.php?t=1876124&highlight=12.04+lts+firewall") to create an iptables firewall (as per 3rd option) but included some additional ports - inc port 21. My machine seems to get part of the way there and then the connection just hangs.

This is my iptables shell script.
```
#!/bin/bash
#Simple Firewall Script.


#Setting up default kernel tunings here (don't worry too much about these right now, they are acceptable defaults)
#DROP ICMP echo-requests sent to broadcast/multi-cast addresses.
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
#DROP source routed packets
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
#Enable TCP SYN cookies
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
#Do not ACCEPT ICMP redirect
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
#Don't send ICMP redirect 
echo 0 >/proc/sys/net/ipv4/conf/all/send_redirects
#Enable source spoofing protection
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter
#Log impossible (martian) packets
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians

#Flush all existing chains
iptables --flush

#Allow traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT


#Creating default policies
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP #If we're not a router

#Allow previously established connections to continue uninterupted
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

#Allow outbound connections on the ports we previously decided.
#iptables -A OUTPUT -p tcp --dport 25 -j ACCEPT #SMTP
#iptables -A OUTPUT -p tcp --dport 110 -j ACCEPT #POP
#iptables -A OUTPUT -p tcp --dport 51413 -j ACCEPT #BT
#iptables -A OUTPUT -p tcp --dport 6969 -j ACCEPT #BT tracker
#iptables -A OUTPUT -p udp --dport 51413 -j ACCEPT #BT
iptables -A OUTPUT -p tcp --dport 21 -j ACCEPT #SSH
iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT #SSH
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT #HTTP
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT #HTTPS
iptables -A OUTPUT -p UDP --dport 67:68 -j ACCEPT #DHCP
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT #DNS


#Set up logging for incoming traffic.
iptables -N LOGNDROP
iptables -A INPUT -j LOGNDROP
iptables -A LOGNDROP -j LOG
iptables -A LOGNDROP -j DROP

#Save our firewall rules
iptables-save > /etc/iptables.rules
```

Could anyone shed any light on what is causing the problem? I am already suffering Unity fatigue as my productivity has nosedived since upgrading!

Thanks for any advice.

---

### Post by captainKrash on 2012-05-16
Additional info, just wacked gftp gui on and this is the connection log:

```

gFTP 2.0.19, Copyright (C) 1998-2008 Brian Masney <masneyb@gftp.org>. If you have any questions, comments, or suggestions about this program, please feel free to email them to me. You can always find out the latest news about gFTP from my website at http://www.gftp.org/
gFTP comes with ABSOLUTELY NO WARRANTY; for details, see the COPYING file. This is free software, and you are welcome to redistribute it under certain conditions; for details, see the COPYING file
View: Not connected to a remote site
Looking up ftp.xxxxxxx.co.uk
Trying server91.xxxxxxx.net:21
Connected to server91.xxxxxxx.net:21
220 This is a private system - No anonymous login
USER xxxxxxx 
331 User xxxxxxx OK. Password required
PASS xxxx
230-User xxxxxxx has group access to:  xxxxxxx  
230 OK. Current restricted directory is /
SYST 
215 UNIX Type: L8
TYPE I 
200 TYPE is now 8-bit binary
PWD 
257 "/" is your current location
Loading directory listing / from server (LC_TIME=en_GB.UTF-8)
PASV 
227 Entering Passive Mode (217,10,138,191,170,154)
Cannot create a data connection: Connection timed out
Disconnecting from site ftp.xxxxxxx.co.uk

```

---

### Post by steeldriver on 2012-05-16
oops nevermind

---

### Post by captainKrash on 2012-05-16
You know what, I don't know ;P

I previously was using GUFW with default allow all out. But decided that perhaps I should tighten things up a bit.

---

### Post by captainKrash on 2012-05-16
I guess then perhaps something like this:

[http://k3mist.com/linux/howto-allow-outgoing-ftp-connections-in-iptables/](http://k3mist.com/linux/howto-allow-outgoing-ftp-connections-in-iptables/)

?

---

