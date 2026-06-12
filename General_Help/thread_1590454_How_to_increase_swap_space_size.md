---
title: "How to increase swap space size?"
date: 2010-10-07
forum: General Help
---

### Post by adummy on 2010-10-07
Hi, New here. :)

I got back to my laptop after dinner and found a blank screen with one line of text saying something about running out of swap space - I tried all kinds of key combinations but nothing worked to bring the desktop back - eventually I pressed and held the power button to shut it down - I suppose this is Ubuntu's version of the "blue screen of death"? :(

I went to System - Disk Utility to make a 2GB free space right after the swap space. Then I tried to make that 2GB free space a swap space partition but it came back with an error. :confused:

Please help. Thanks! :)

---

### Post by MegaLoler on 2010-10-07
Can you boot into Ubuntu at all?  If not, maybe you could create a gparted live cd, and boot that and try gparted.

---

### Post by adummy on 2010-10-07
> **MegaLoler said:**
> Can you boot into Ubuntu at all?  If not, maybe you could create a gparted live cd, and boot that and try gparted.

Yes I can boot into Ubuntu but the Disk Utility had trouble creating the partition. I will try gparted. By the way can ubuntu use two swap partitions or just one?

---

### Post by andrewthomas on 2010-10-07
You can have as many as you want.  They just need to be listed in /etc/fstab.

---

### Post by adummy on 2010-10-07
> **andrewthomas said:**
> You can have as many as you want.  They just need to be listed in /etc/fstab.

Thanks that helps.

I am in deeper trouble now. :cry: I updated the system, which required a restart. Before doing that I thought I would give Disk Utility one more try. This time it did not complain but made a tiny ~ 500 kB partition of "unknown" type. I thought that was odd and went ahead deleted that partition. Then after restarting came the dreaded blank screen saying something like 
unknown filesystem
grub rescue>
:confused:
I tried to use the USB key that worked before to boot from the USB key. It seemed going well all the way up to the screen showing "Ubuntu" in big letters with some dots below changing color. But then again blank screen and eventually the laptop shut itself off. :(

---

### Post by adummy on 2010-10-09
Continued here:
[http://ubuntuforums.org/showthread.php?t=1590694](http://ubuntuforums.org/showthread.php?t=1590694)

---

