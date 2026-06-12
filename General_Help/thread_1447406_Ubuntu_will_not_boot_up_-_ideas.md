---
title: "Ubuntu will not boot up - ideas?"
date: 2010-04-05
forum: General Help
---

### Post by jensenguy on 2010-04-05
I have a 9.10 ubuntu install on my laptop, 32 bit. Its been in for a couple months, never had any problems until today. When I first start it up, I get to the Grub loading.. message, then it bumps me to a recovery options list  - which wont let me select a boot mode or go any further. I tried booting off of my install disc, which loads fine, and Im actually just running directly on that right now. So Im guessing something got corrupted or lost on my hard drive.

What are my options beyond just wiping it out and starting fresh? Is there any utilities I can use to check for errors or repair the installation? I tried a generic hard disk check on my BIOS screen and it came up clean.

thanks for any help!
jim

---

### Post by 98cwitr on 2010-04-05
using the live cd mount the drive and find, then post, your menu.lst file. Sounds like a problem with grub...you could also run a fsck on the drive

---

### Post by jensenguy on 2010-04-05
Where is menu.lst normally located? I tried a search on the drive and didnt come up with anything. Also with fsck, dont I have to select the recover mode from that menu I cant do anything with to be able to run it?

thanks

---

### Post by 98cwitr on 2010-04-05
my bad, i see you're on 9.10...look at this
[http://ubuntuforums.org/showthread.php?t=1307775](http://ubuntuforums.org/showthread.php?t=1307775)

---

### Post by djoxyk on 2010-04-05
Check this page for Grub howto
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Basically you can load from your live CD and update grub from terminal (see section for Command line)

[http://linuxmint.com/wiki/index.php/How_to_repair_your_grub](http://linuxmint.com/wiki/index.php/How_to_repair_your_grub)
This page is about repairing grub.

---

