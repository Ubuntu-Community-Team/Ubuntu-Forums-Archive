---
title: "How to Clone Multiboot Hard Drive"
date: 2009-06-30
forum: General Help
---

### Post by undoIT on 2009-06-30
I have a hard drive with Windows XP, Ubuntu and several other Linux distros installed and all of them boot with grub. Is there a way to clone the entire hard drive with all partitions and MBR to another hard drive?

---

### Post by louieb on 2009-06-30
[Clonezilla]("http://www.clonezilla.org/") makes an exact copy.

or I use [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") can comes close - you can copy and paste partitions from one drive to the other. Resize them at the same time. Then you will have to setup the new drive to boot GRUB.

---

### Post by undoIT on 2009-06-30
Nice! Thank you for the links. I'll try clonezilla and if that doesn't work, take a shot with Gparted.

---

### Post by bodhi.zazen on 2009-06-30
You can use any number of techniques.

If you need an alternate, take a look at dd (and variants).

---

### Post by t4thfavor on 2009-06-30
My vote is for ddrescue, I have used it a number of times, and it always worked for me.

---

