---
title: "Ubuntu install getting frozen at &quot;Select a disk&quot; screen"
date: 2006-06-09
forum: General Help
---

### Post by nameiwantistaken on 2006-06-09
I'm installing Ubuntu onto a 36Gb Raptor that I know is working (was running another OS fine and I just ran the WD check utility) and the install goes fine until it gets to step 5 of 6 Select a Disk.  At this point, the application just seems to go into a loop.  The cursor just spins when on this window.  I've removed everything I can from the system and have no idea why this is working this way.  Can anyone think of a workaround?

---

### Post by nameiwantistaken on 2006-06-09
It seems that the problem in question is associated with having a DVD IDE master and a sata drive.  I fixed that issue, but now it will only load onto the IDE drive.  Is anyone else having sata compatibility problems?  I downloaded an image yesterday.

---

### Post by Psmckinley on 2006-06-10
I am having the same problem.

The computer gets to Select a disk, it runs through the partitioner and nothing happens.  I tried running Gparted and it found nothing (earlier).  

I have an 80GB SATA Hard Drive, basic CD-ROM (I broke my DVD drive tonight).  I have been running Windows XP, and wanted to do a full switch.

Running AMD Athlon64 3700+
2 GB RAM

---

### Post by nameiwantistaken on 2006-06-19
My problem now seems to be related to the south bridge chip from Via.  It is a VT8251 chipset.

---

### Post by amar2d4 on 2007-02-02
hey!

I have the same problem it freezes at the "Select a disk'.

I left it for the night at office.....it never finished.

I selected "install ubuntu in safe graphics mode" that why it reached this stage..earlier at normal install it froze when language was selected.

I feel it has something to do with the Graphics drivers & Ubuntu.

Mine is a Dell Optiplex GX520 ,256 MB ram,30 Gb HDD machine.

---

