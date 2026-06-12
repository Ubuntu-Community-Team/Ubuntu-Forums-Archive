---
title: "Command to see what my rtl chipset is please"
date: 2010-09-16
forum: General Help
---

### Post by jimbotz on 2010-09-16
Hi guys completey new to Ubuntu.
Could some kind person please tell me the command to show me if i have a RTL8187B or RTL8187L inside my AWUS036H, i have searched all over Google but cant find an answer.

Thank you

---

### Post by pebo on 2010-09-16
```
lspci | grep Network
```should give you your wireless
```
lspci | grep Ethernet
```should give you your ethernet

---

### Post by cascade9 on 2010-09-16
8187L according to this page- 

[http://dplanet.biz/alfa.com/images/AWUS036H-11g%20high%20power%20USB%20adapter-00.pdf](http://dplanet.biz/alfa.com/images/AWUS036H-11g%20high%20power%20USB%20adapter-00.pdf)

---

### Post by jimbotz on 2010-09-16
That command gives me my Ethernet, i need to see the adapter that is connected to wla0.
I have read there are fakes of my wireless adapter doing the rounds and need to see if it is a RTL8187L.

Thanks

---

### Post by cascade9 on 2010-09-16
lshw should give you a (huge) list of all the hardware in your machine ;)

---

### Post by jimbotz on 2010-09-16
Cascade it shows this for wlan0 with that command.

*-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:ca:3f:1f:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

I need to see RTL8187L or RTL8187B

Thanks

---

### Post by QLee on 2010-09-16
[QUOTE=jimbotz]That command gives me my Ethernet, i need to see the adapter that is connected to wla0[/QUOTE]

Singular, command? There were two commands given in that post, one shows ethernet interface, one shows wireless interface. At least, that what those two commands do on my system.

You could also look through your dmesg log file, there will be lines where it is found and configured during the boot sequence.

---

### Post by jimbotz on 2010-09-16
Ah Ha [QLee]("http://ubuntuforums.org/member.php?u=934089") that worked, but i see what i was not hoping to see.

732.270552] phy0: hwaddr xxxxxxxxxxx, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2.

It shows it as a B version, and when i brought it,  i got it from Ebay it said it was an L.

Thanks guys for your help

---

