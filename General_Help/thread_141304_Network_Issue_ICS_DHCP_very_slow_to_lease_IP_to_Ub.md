---
title: "Network Issue: ICS DHCP very slow to lease IP to Ubuntu"
date: 2006-03-08
forum: General Help
---

### Post by somerville32 on 2006-03-08
Hello,

 I'm having a networking issue with Ubuntu. In our home, a Windows XP Box uses ICS to share its internet connection with our Win98/Ubuntu Linux Dual boot. Windows 98 is able to boot and lease an IP address quickly and effortlessly while with Ubuntu I have to sit staring at the monitor for a few hours typing ifup then ifdown until I finally get leased an ip. Also, if memory serves me correctly, I didn't have this issue with any other Linux distributions that I have tried.

In my attempt to resolve this issue, I've tried modifying the dhcp client config file and changing the rate at which is spams the dhcp server with a request - no effect. It also appears that my chance of success has no apparent pattern or any identifiable factors that I can find. 

If the only solution you can provide is to move to a router then please do not post as I'm already in the process of doing so. However, I suspect that others might be experiencing the same problem and I would like to find a solution in case moving to a router isn't a viable option for them.

Thank you for your time,

Cody A.W. Somerville

---

### Post by Garyu on 2006-03-08
I had similar problems on my parents computer. Their "/etc/network/interfaces" looked like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet dhcp
        network 213.67.255.249
        broadcast 213.67.255.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

```

So what I did was, first of all, to set up dhclient to load on startup (don't remember how I did that though, not in sessions but earlier in the boot. I found a howto that gave directions on how to do this by creating a file called local and just inserting "dhclient".

Secondly, I modified the "/etc/network/interfaces" to contain:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Oh, and they have an ADSL modem, which I think is part of their problem, because Ubuntu did strange things in the network setup on install and I think this is because of the ADSL. Now it works smoothly though. :cool:

---

### Post by somerville32 on 2006-03-08
Thank you for your reply. 

The following is my /etc/network/interfaces

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

auto eth0
iface eth0 inet dhcp


I tried commenting out the mapping hotplug section but it had no effect so I don't think we have the same problem.

However, I did find something very interesting. It appears that it works fine if I disable and then re-enable the network card on the xp box. However, if I ifdown and then ifup again it doesn't work (unless I disable and re-enable again during ifup). I also get the following when I ifdown:

> 
root@cody1:/home/cody# ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 7879
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:10:a7:29:5e:eb
Sending on   LPF/eth0/00:10:a7:29:5e:eb
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.


I've tested this several times and I'm pretty sure my findings are conclusive. 

On another note, here is a copy and paste of /var/log/syslog

> 
localhost dhclient There is already a pid file /var/run/dhclient.eth0.pid with pid 0
localhost dhclient Internet Systems Consortium DHCP Client V3.0.2
localhost dhclient Copyright 2004 Internet Systems Consortium.
localhost dhclient All rights reserved.
localhost dhclient For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
localhost dhclient 
localhost dhclient sit0: unknown hardware address type 776
localhost dhclient sit0: unknown hardware address type 776
localhost dhclient Listening on LPF/eth0/00:10:a7:29:5e:eb
localhost dhclient Sending on   LPF/eth0/00:10:a7:29:5e:eb
localhost dhclient Sending on   Socket/fallback
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
localhost kernel [4295605.132000] 0000:00:10.0: tulip_stop_rxtx() failed
localhost kernel [4295605.132000] eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
localhost kernel [4295612.258000] eth0: no IPv6 routers present
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
localhost dhclient DHCPOFFER from 192.168.0.1
localhost dhclient DHCPREQUEST on eth0 to 255.255.255.255 port 67
localhost dhclient DHCPACK from 192.168.0.1
localhost dhclient bound to 192.168.0.107 -- renewal in 250 seconds.
localhost dhclient DHCPREQUEST on eth0 to 192.168.0.1 port 67
localhost dhclient DHCPACK from 192.168.0.1
localhost dhclient bound to 192.168.0.107 -- renewal in 242 seconds.


---

### Post by somerville32 on 2006-03-08
I've switched to a router and the issue is resolved. I talked with a few friends of mine and they said they had the exact same problem with their all-window network, so it appears that the problem is that of Windows and not Ubuntu - which is too bad.

So... If anyone else has similar problems, don't use Windows XP ICS! :D

---

### Post by ChrisNiemy on 2007-10-06
(I'm quite a noob concerning network, but the following steps solved some issues for me, maybe it will also help in your case)

Try to add your hostname (see /etc/hostname) to the loopback line (first line usually) in /etc/hosts:

before:
```
127.0.0.1 localhost
(...)
```

after (e.g. my hostname is "kringel")
```
127.0.0.1 localhost kringel
(...)

```

This might help, but seems to be another issue

Also change the beginng of /etc/network/interfaces from
```
auto lo
iface lo inet loopback
(...)

```

to
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
(...)

```

then ```
sudo /etc/init.d/networking restart
``` or reboot.

otherwise (mabye) try to decrease the timeout (it's an uncommented line) in /etc//etc/dhcp3/dhclient.conf

or something is wrong with /etc/iftab

also might be interesting:
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)
[http://ubuntuforums.org/showthread.php?t=179745](http://ubuntuforums.org/showthread.php?t=179745)
[http://ubuntuforums.org/showthread.php?t=180447](http://ubuntuforums.org/showthread.php?t=180447)

---

