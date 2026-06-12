---
title: "Intel Ethernet 82557/8/9 &quot;e100&quot; Problem"
date: 2006-04-04
forum: General Help
---

### Post by muraii on 2006-04-04
Hi,

I have recently installed Ubuntu 5.10, and have sifted through all the posts about why I need to skip (CTRL+C) the hotplug system loading step, and have installed 5.10 with the "noapic nolapic" options.  I have checked the network properties of my card via Gnome, and activated the card (so I thought) multiple times.  I've run "lsmod" to make sure the e100 module is loaded, and it appears it is.

I still cannot get network access.

I've checked the cables, and they appear fine.  I get a connection light on my (old but operable) D-Link router when connecting to this (older P3-700) machine.  I still cannot get network access.

When I click "Activate" in the network utilities dialog in Gnome, the system thinks for a while (a minute or two) and then shows eth0 to be active.  I try to access anything (via URL or IP address), even the router, and get nothing.  I've manually entered the DHCP information, as well as tried to assign an IP by the router, and nothing.

Is there one or more setting files I can check, and whose output I can post, to see exactly what the problem is?  I've tried searching the forum for days, and found quite a few things to try (as noted above) but with no luck.  I RTFM.

Thank you for any help you can offer.

Daniel

---

### Post by muraii on 2006-04-04
Here's an update:

According to [this link]("http://www.linuxquestions.org/questions/showthread.php?p=1776506#post1776506"), I need to run through a couple of hoops to effectively disable designed functionality on this card to get Linux to work with it.  I mean, the right module (e100) is listed in the lsmod output, the cable is good, and here is the output from ifconfig -eth0 (transcribed):

```

Link encap:Ethernet  HWaddr  00:90:27:EB:BA:22
BROADCAST MULTICAST  MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

```

I don't know what to do next.  I don't have any extra cards lying around to try, nor do I have any other machines in which to try this one.  It seems to be interacting *some* with the machine, e.g. the router has a light showing it notices something's plugged in and powered; but this machine isn't in the DHCP log so far as I can tell, and "host <anything>" returns nothing but "no servers could be found".

Any help?

---

