---
title: "Ethernet Device Problem"
date: 2006-03-22
forum: General Help
---

### Post by elder68 on 2006-03-22
When I go to the Network settings in the Control Centre of KDE, it searches for the ethernet device - eth0 - and returns with the message that this device is disabled. Can somone help me to enable the eth0 device.

Thank you.

Bill.

---

### Post by njf on 2006-03-22
In Konsole, type :

```
sudo ifup eth0
```

---

### Post by elder68 on 2006-03-22
[QUOTE=njf]In Konsole, type :

```
sudo ifup eth0
```[/QUOTE]

Thank you for this, the result of the above was:

Ignoring unknown interface eth0=eth0

Bill.

---

### Post by Barrakketh on 2006-03-22
[QUOTE=elder68]Thank you for this, the result of the above was:

Ignoring unknown interface eth0=eth0

Bill.[/QUOTE]
Post the contents of /etc/network/interfaces.

---

### Post by jamesr on 2006-03-22
also post output of

sudo ifconfig -a

---

### Post by Kyle- on 2006-03-24
I'm bumping this because I'm having the exact same problem.  
Here is my etc/networks/interfaces info

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

```

And here is the result of sudo ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 08:00:46:4E:82:80
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:25094 (24.5 KiB)  TX bytes:25094 (24.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0E:3B:02:8A:34
          inet addr:192.168.2.131  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:3bff:fe02:8a34/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:354 txqueuelen:1000
          RX bytes:4714553 (4.4 MiB)  TX bytes:1155530 (1.1 MiB)
          Interrupt:9 Base address:0xc000

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Thanks ahead, 

Kyle-

---

### Post by elder68 on 2006-03-24
Kyle got in ahead of me with a similar problem. Following are my two files that were requested. Bill.

etc/network/interfaces:
------------------------------

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

Contents of: sudo ifconfig -a
-------------------------------------

eth0      Link encap:Ethernet  HWaddr 00:04:E2:04:E9:D9
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xb400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:850751 (830.8 KiB)  TX bytes:850751 (830.8 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:206.191.1.89  P-t-P:64.26.173.102  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:665460 (649.8 KiB)  TX bytes:91638 (89.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Kyle- on 2006-03-24
Sorry William, I don't mean to hijack your thread.  I just think it might be easier to kill two birds with one stone.

K-

---

### Post by wanger123 on 2006-03-24
Hey guys, I think you are missing this bit: iface eth0 inet dhcp
See my file below


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
iface eth0 inet dhcp

```

If you have a static address it should look like this: (Obviously you put your own ip, gateway etc details in where the ????'s are)

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
iface eth0 inet static
	address 134.???.???.???
	netmask 255.???.???.???
	network 134.???.???.???
	broadcast 134.???.???.???
	gateway 134.???.???.???
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 134.???.???.??? 134.???.???.???
```


cheers
wanger

---

### Post by Kyle- on 2006-03-24
Thanks Wanger!  That worked for me.  For some reason enabling the eth0 using the KDE control center didnt' work so as root I opened etc/network/interfaces and added this to the end ```
# The primary network interface
iface eth0 inet dhcp 
``` I rebooted and it worked.  Thanks again.

---

### Post by wanger123 on 2006-03-24
Cool! Good stuff Kyle-. It's just so satisfying when you get something working after messing with it for a while. Don't you agree? Especially something as intrinsic and vital as networking.

cheers
wanger

---

### Post by elder68 on 2006-03-24
Thank you, as Kyle did, I did the same. Under the KDE control centre it showed my eth0 card as being disabled.

Then with "sudo ifup eth0" I now show the eth0 as being configured. Hmm, go figure!

My efforts with all this is to get my wireless high speed working. It is an always on system that is part of a network. The connection to my computer is through the network card.

When I connect the wireless to my Windows 98 box, I did nothing at all and the wireless connection was fine.

On the same box I had installed Suse 9.3 as a looksee sort of installation. So I tried the wireless connection on that OS, I did nothing and it worked fine.

Connected to Kubuntu, the wireless connection does nothing. This is being written on my old dialup system.

Any help would be appreciated.

Bill.

---

### Post by chylee on 2006-03-25
I'm trying to delete this message I put it in the wrong thread

---

### Post by jamesr on 2006-04-05
Hi Elder68,

Do you still have the network problem

---

### Post by elder68 on 2006-04-06
[QUOTE=jamesr]Hi Elder68,

Do you still have the network problem[/QUOTE]

Thank you for your note. I upgraded to Kubuntu 5.10 and set  up the networking as it was installing. Everything is fine.

---

### Post by tmcclellan on 2007-12-07
OK, I'm a complete linux n00b, and can't for the life of me get my ethernet up.

Short story, I was wireless, and never could get online. For other reasons, I moved the PC to where it was wired, and it fired right up, no worries.

A few weeks later, I pulled out the wifi card, and lost my ethernet connection in the process, and now can't connect to save my life.

I'm using Kubuntu Fiesty, and I've read this thread up and down, as well as the linked threads.

Here's my interfaces file:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

address 127.0.0.1
netmask 255.0.0.0
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
address 192.168.15.100
netmask 255.255.255.0
gateway 192.168.15.1

auto eth0

I have no issues on the same PC in XP, and configured my eth0 interface with the same settings I use in XP.
Any help would be greatly appreciated.

EDIT:
And sorry for bumping an 18 month old thread. :o 
But at least I searched first, I just didn't read the dates.

---

