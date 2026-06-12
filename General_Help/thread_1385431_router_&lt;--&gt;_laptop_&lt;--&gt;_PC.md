---
title: "router &lt;--&gt; laptop &lt;--&gt; PC"
date: 2010-01-19
forum: General Help
---

### Post by Xog on 2010-01-19
I really don't understand the point of the Networking/Wireless forum section.. hardly ever see anyone there.


Let me catch you up to speed.

I have:
I have a wireless router.
I have a laptop that can connect to the wireless router.
I have a PC that is currently wired to my laptop.
I have edited sysctl.conf and uncommented net.ipv4.ip_forward=1 (on the laptop)
I have done "sysctl -a"

I need:
I need to have the PC connect to the internet using the wireless from my laptop.

For reasons beyond my control I cannot move my PC to the router or modem for easier wired access. After I have internet and have run a few programs I can undo all of this and access it wirelessly from the PC.

Laptop's 'Auto eth0'
IPv4 Settings: 
Method: Manual
Address: 10.1.1.1
Netmask: 255.255.255.0
Gateway: 0.0.0.0

PC's 'Auto eth0'
IPv4 Settings:
Method: Manual
Address: 10.1.1.2
Netmask: 255.255.255.0
Gateway: 10.1.1.1

The two computers can ping eachother.
The laptop can ping the router.
The laptop can ping the PC.
The PC can ping the laptop and router.
The PC can ping 4.2.2.1.
The PC cannot open webpages.

I install dnsmasq on the laptop.

laptop can ping PC
PC can't ping laptop or anything.

laptop is running ubuntu via LiveCD (32-bit).
PC is running ubuntu 9.10 64-bit
I left them on while I was at work so I didn't have to re-do any settings.

I'm now at work and I get home in 2.5 hours. Please post suggestions or ideas on why it's not working.

---

### Post by mihamil on 2010-01-19
Will this help

[http://doctormo.wordpress.com/2009/12/06/ubuntus-internet-connection-sharing/](http://doctormo.wordpress.com/2009/12/06/ubuntus-internet-connection-sharing/)

---

### Post by roadtripdave on 2010-01-19
Maybe the following link will help point you in the right direction.

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Regards

---

### Post by Xog on 2010-01-19
> **mihamil said:**
> Will this help

[http://doctormo.wordpress.com/2009/12/06/ubuntus-internet-connection-sharing/](http://doctormo.wordpress.com/2009/12/06/ubuntus-internet-connection-sharing/)

I was advised not to use that method but I'll give it a shot when I return home if no other methods arise to continue where I left off.

[quote=roadtripdave]Maybe the following link will help point you in the right direction.

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Regards [/quote]
perhaps ipmasq is something I need. I'll give that a shot first, however that post is 5 years old.

---

