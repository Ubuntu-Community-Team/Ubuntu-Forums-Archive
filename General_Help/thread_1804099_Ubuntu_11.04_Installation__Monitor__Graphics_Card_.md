---
title: "Ubuntu 11.04 Installation : Monitor / Graphics Card problem"
date: 2011-07-14
forum: General Help
---

### Post by gurpreet470 on 2011-07-14
I am trying to install ubuntu 11.04 from live CD on my dell inspiron 1520, running Win 7.
However, as soon as the system boots from the CD, the screen starts showing vertical colored lines, and I cannot read a word. From what little I can think, this is issue dealing with the higher resolution / graphics card (Nvidia 8600M GT). Native resolution of my monitor is 1440X900
I tried giving some additional parameters during boot (just added towards the end) :

fb=false viedo=video16:off --> It didn't work

vga=771 --> It didn't work

The installation is definitely working behind the scenes, because if I keep the screen as it is for 5-7 min, I can listen to some nice sounds coming, confirming something worked.

Can someone help me on this?

My first post, so be nice :)
Thanks

---

### Post by dino99 on 2011-07-14
you might browse the Dell subforum

actual kernel directly deals with X, so xorg.conf often breaks things (no need by default)

---

### Post by Mark Phelps on 2011-07-14
> **gurpreet470 said:**
> I am trying to install ubuntu 11.04 from live CD on my dell inspiron 1525, running Win 7.


Presuming you still want to use Win7, do NOT force an install -- at least, not yet.

Dell is famous for configuring PCs preloaded with Win7 with the maximum number of 4 primary partitions.  So, to check for this, if you can get the boot from the LiveCD working, open a terminal and enter "sudo fdisk -lu (that's a lowercase L, not a one).  This will list out the partitions on your hard drive.  If there are 4 partitions there already, you have a major problem as that is the maximum you can have.

Also, if you have an optical drive on your PC, BEFORE you do the dual-boot install, launch the Backup feature in Win7 and use it to create and burn a Win7 Repair CD.  That will come in handy later should you need to repair the Win7 boot loader.

---

