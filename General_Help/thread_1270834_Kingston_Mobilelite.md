---
title: "Kingston Mobilelite"
date: 2009-09-20
forum: General Help
---

### Post by xsilvergs on 2009-09-20
Hi,

I have a Kingston Mobilelite USB card reader which has work under Ubuntu since I started with Ubuntu a year ago.

Suddenly it has stopped being recognised when plugged in, I have tried it in all three of my Ubuntu PC's and it is not recognised by any of them anymore.

If I plug it into any Windows XP PC it is found and displayed in Explorer and I'm able to access it.

lsusb reports this
tony@BlackUbuntu:~$ lsusb
Bus 001 Device 003: ID 0cf2:6225 ENE Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

with or without the card reader plugged in.

Any ideas on what I should do next?

Thank you

---

### Post by xsilvergs on 2009-10-20
I have still not managed to get this working.

What should I try next?

---

### Post by P4man on 2009-10-20
Thats odd.. to put it mildly. Since this happens on 3 different machines, i guess we can rule out a hardware issue on the pc side. on the card reader side seems very unlikely too as it works in windows.. which leaves a software problem.

Are all 3 ubuntu's running the same version and kernels? Do you upgrade them simultaneously? I guess I would try a live cd, see if it works there. If it does, perhaps try an older kernel if you have any in your grub. If you manage to find the cause or kernel, file a bug report. OTOH its kinda weird you would have this problem on 3 machines and no else would have it? Are those 3 machines identical by any chance?

---

### Post by xsilvergs on 2009-10-20
Hi P4man,

All PC's are differnt, a twin core desktop, a pentium 3 desktop, a twin core laptop and a NC10 running UNR.

All PC's are the latest Kernel.

I'll try a live CD and report back.

Thanks

---

### Post by xsilvergs on 2009-10-22
It's working.

Just by chance I booted the twin core desktop with the drive plugged in and after a couple of minutes it appeared on screen. I've just been through the same procedure on the NC10 and it is now detected whenever it plugged in.

I don't understand why but it works.

Thanks for suggestions.

---

