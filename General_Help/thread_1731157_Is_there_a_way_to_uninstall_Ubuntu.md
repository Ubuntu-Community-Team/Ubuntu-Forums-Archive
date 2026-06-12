---
title: "Is there a way to uninstall Ubuntu?"
date: 2011-04-16
forum: General Help
---

### Post by TacticalApe on 2011-04-16
I'm thinking about installing Ubuntu 10.10 onto an external hard drive (i'm sick of windows 7) and my EHD has about 1tb of space. I just want to know how to uninstall it, just in case. Is there a way?

---

### Post by lmarmisa on 2011-04-16
This is very easy to uninstall Ubuntu from an external hard drive. For example, you could format the partitions involved in Ubuntu.

If you take the decision of installing Ubuntu, I recommend to define your partitions manually. For example:

1) A ext4 partition with a size of 10-50 Gbytes for Ubuntu (/).
2) A swap partition with a size of 2X your RAM.
3) A big NTFS partition for data.

And the most important thing: choose the manual option for the definition of partitions during the installation and **install the GRUB loader in the external hard drive.** **Do no install GRUB in any internal hard drive!!!!!.**

---

### Post by K_45 on 2011-04-16
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

If you want to uninstall it, format it in Gparted.

---

### Post by TacticalApe on 2011-04-16
> **lmarmisa said:**
> For example, you could format the partitions involved in Ubuntu.

How do you do that? I've never used Ubuntu or any linux distro before, I'm a total noob when it comes to this stuff.

---

### Post by K_45 on 2011-04-16
You would select manual partitioning and choose the options you wanted.

---

### Post by lmarmisa on 2011-04-16
> **TacticalApe said:**
> How do you do that? I've never used Ubuntu or any linux distro before, I'm a total noob when it comes to this stuff.

Do not worry about my comment. Your Ubuntu system will use two partitions. If you wish to remove Ubuntu, you simply have to remove (or reformat) these two partitions from your external hard drive. You can remove/format them from Windows 7 (administration tools) or using an Ubuntu Live CD and the tool GParted.

---

### Post by Thewhistlingwind on 2011-04-16
> **TacticalApe said:**
> How do you do that? I've never used Ubuntu or any linux distro before, I'm a total noob when it comes to this stuff.

The drive should have a button in windows when you right click that says "format". As long as only ubuntu is on there, and you don't have any files you need, it's safe to wipe it.

---

### Post by TacticalApe on 2011-04-17
well I installed ubuntu and it messed things up, now I'm going to uninstall then reinstall, and I formatted the EHD and ubuntu is still there.

---

### Post by oldos2er on 2011-04-17
Can you follow the instructions here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the RESULTS.txt file so we can see what's going on with your system?

---

### Post by TacticalApe on 2011-04-17
Well, nevermind. I've got it all sorted out now.

---

