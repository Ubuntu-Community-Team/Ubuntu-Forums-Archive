---
title: "Not connecting to internet"
date: 2010-07-03
forum: General Help
---

### Post by cracklins on 2010-07-03
Good afternoon,

I created a Live CD with Ubuntu 10.4 Desktop, in which everything seems to work except Firefox, or internet connections in general. I've tried several other Linux distros with the same results. The DSL modem is on and working (USB Westell Wirespeed duel connect modem), works with Windows XP (native OS on this computer) but not with this live cd. 

Ive been inside the network manager, and have only one connection setup which is DSL and automatically connect. But when it looks for a connection, none is found (the tab on the upper right corner of the desktop with the exclamation mark).

The live cd connects at work, but it's through a server and connected to that via ethernet, so that's a completely different setup.

From searching this forum, I've seen countless other instances of connectivity issues, and it all seems to involve hours of testing, command line editing, and other things that more often than not produce no results. 

Any hope?

thanks! :KS

---

### Post by Rubi1200 on 2010-07-03
Hi and welcome,

on the LiveCD, go to Applications > Accessories > Terminal and copy the output from:

```
 cat /etc/network/interfaces
```

Post back here and we can try and take it from there.

---

### Post by Iowan on 2010-07-03
Does the machine get an IP address? (**ifconfig -a**)

---

### Post by cracklins on 2010-07-03
Here's the result from Terminal:

cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by nautica17 on 2010-07-03
> **cracklins said:**
> Here's the result from Terminal:

cat /etc/network/interfaces
auto lo
iface lo inet loopback
It looks like you're missing eth0.

---

### Post by cracklins on 2010-07-03
results of ifconfig:

ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:60:0f:82:0b:53  
          inet6 addr: fe80::260:fff:fe82:b53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:202 dropped:0 overruns:0 frame:202
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2662 (2.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8016 (8.0 KB)  TX bytes:8016 (8.0 KB)

---

### Post by nautica17 on 2010-07-03
You could add the following to your interfaces file and see if it helps any:

auto eth0
iface eth0 inet dhcp


If that doesn't work, just remove the lines. Note that you have to restart your connection to put this into effect. (Restart computer should do).

Edit: You said Live CD... so I think my suggestion wouldn't work now that I think of it.

Edit 2: Well... if you edited the interfaces file and did a network restart from within the LiveCD, then maybe things could work. 
Try this after editing the file:
sudo /etc/init.d/networking restart

---

### Post by Iowan on 2010-07-03
Unless your machine is supposed to have a static IP address, try **dhclient eth0** - you'll *probably* see something like:```
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by cracklins on 2010-07-12
I'm back, and thanks for advice. 

However, after reading a few dozen threads and articles, it appeared Linux based Live Cd's didn't really get along well with usb connected modems. So, rather than spend time experimenting with settings, I installed an ethernet card and things worked fine, for two days. 

After booting from Windows XP into a series of Live CD's (I'm looking at all the Linux distros), I noticed several hours later when I went to access the internet through one of them that the ethernet connection was gone - no light on the modem. The internet light was on, but not the ethernet light.

So, I booted back into XP and the light was on, no connection problem. As soon as I restart, the second XP shuts down and I'm in the Dell BIOS between boots, the ethernet light goes off. 

Wow - worked in the beginnng, but something killed it for Live CD's. A little research reveals similar instances by other users being somewhat rectified by cold, and I mean freezing, Arctic cold, boots. So I guess I'll see what happens tonight, 24 hours later. That's cold, man....

Thanks Again! :-\"

---

