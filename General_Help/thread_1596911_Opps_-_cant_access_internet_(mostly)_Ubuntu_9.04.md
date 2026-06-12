---
title: "Opps - cant access internet (mostly) Ubuntu 9.04"
date: 2010-10-14
forum: General Help
---

### Post by fisheater on 2010-10-14
Hi all,

Problem: Using ubuntu 9.04 64 bit, attempted to install wireless card to desktop. Wasn't able to get wireless to work, now LAN isnt working.

I am unable to use the internet from the desktop (mozilla, update, ping, etc) BUT the strange thing is that I can NX nomachine into my desktop.

This boggles my mind, I can get in via the Nx but am unable to get out. So I know my lan card is working.

Question: I must have changed a setting when I was goofing around with the wireless install (via network, network tools). Is there a way to 'flash' my network back to fresh install? In other words, how do I restore it to its previous unconfigured setting.

The threads I have read havent been able to help me to date.

Thanks for your help!

FE

---

### Post by fisheater on 2010-10-15
The fix: sudo dhclient eth0

(from: [http://ubuntuforums.org/showthread.php?t=1264703](http://ubuntuforums.org/showthread.php?t=1264703))

The power of open source is superb.

Thanks for the help.

FE!

---

### Post by fisheater on 2010-10-16
Ok, spoke too soon.

Problem: cant use net, unless using sudo dhclient eth0 cmd first.

Then any relog, or the certificate expires, have to redo sudo dhclient eth0.

Any suggestions on permanent fix?

thanks!

---

### Post by fisheater on 2010-10-21
Good news = able to login remotely via Nx to my desktop.

Bad news = still have to 'sudo dhclient eth0' to access the internet from my Nx instance of my desktop on a remote computer. 

It the big picture, the system works. But would like to have a fix for my oops!

Any suggestions on a patch for my network manager mixup?

thanks!

FE

---

### Post by fisheater on 2010-10-22
Update: I upgraded from 9.04 to 9.10 to 10.04  but the problem persists.

---

### Post by fisheater on 2010-10-23
update:

using 'sudo dhclient eth0' i get:

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:13:d4:7f:1d:dc
Sending on   LPF/eth0/00:13:d4:7f:1d:dc
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.199 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.199 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.199 from 192.168.1.1
bound to 192.168.1.199 -- renewal in 38668 seconds.

This gets my internet active on my desktop, but only when i use the 'sudo dhclient eth0' command.

I have it set up as a static IP so I can log in to my desktop remotely.

eth0 is missing from my network manager.

I tried following this 'http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9652128' but no luck.

Thanks for following my thread.

FE!

---

### Post by Swiftjay on 2010-10-23
> **fisheater said:**
> update:

using 'sudo dhclient eth0' i get:

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:13:d4:7f:1d:dc
Sending on   LPF/eth0/00:13:d4:7f:1d:dc
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.199 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.199 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.199 from 192.168.1.1
bound to 192.168.1.199 -- renewal in 38668 seconds.

This gets my internet active on my desktop, but only when i use the 'sudo dhclient eth0' command.

I have it set up as a static IP so I can log in to my desktop remotely.

eth0 is missing from my network manager.

I tried following this 'http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9652128' but no luck.

Thanks for following my thread.

FE!


Wait, so what your saying is that eth0 won't get an ip unless you use that line, you could manually configure the ip address

ifconfig eth0 192.168.1.39 up netmask 255.255.255.0 

you'll need to set your default gateway and since your gw is 1.1 you can

route add default gw 192.168.1.1

if it doesn't change the default gateway to 1.1 you could always vi /etc/resolv.conf to change your nameserver to your router address.

now, as for your wireless you could check to see if ubuntu even picks up the wireless card by checking mii-tool.

leme know if that solves the problem with your ip address permently.  Btw 39 was just an example you can change it to what ever you want it to be.

---

### Post by fisheater on 2010-11-07
Great stuff, I was away for a bit and have yet to try the fix.

I'll have a go tonight and let you know what happens.

Thanks again!

FE

---

### Post by fisheater on 2010-11-17
thanks for all your help, nothing to date had helped.... except:


i installed a new gigabit network card, then it automoutned at etho1 and works.

Not solved by software, but by hardware.

Thanks

FE

---

