---
title: "Install Hangs on Grub Install"
date: 2006-03-29
forum: General Help
---

### Post by ZAxisMapping on 2006-03-29
I've spent hours reading various threads here (which are very helpful), but don't exactly apply to my problem.

Essentially, I am experiencing the following known bug:
[https://launchpad.net/distros/ubuntu/+source/apt-setup/+bug/23799]("https://launchpad.net/distros/ubuntu/+source/apt-setup/+bug/23799")

But, it occurs during regular install too (not just expert), AND, still hangs if I say "No" to "Add another apt source?"...contrary to what Colin Watson says at the bottom.

The problem is: Grub is not installed in any form (grub is not installed properly on the MBR **and** the package is not there), therefore all the advice about chrooting the / partition and running grub-install isn't working.  There is no grub-install under /sbin/, or anywhere according to find.

When I try the live CD, I can't even:

```
apt-get install grub
```

I have an ASUS A8N32-SLI, 2 sata drives, winblows on sda and ubuntu on sdb.  Does anyone know how I can install grub, so I may execute:

```
grub-install /dev/sda
```

I'm so close!!

---

### Post by trent dillman on 2006-03-29
Install LILO instead. :-)

---

### Post by ZAxisMapping on 2006-03-30
Unfortunately, the same behavior occurs when installing lilo during the install process.  I can tell it's always hangs in the same spot by cntl-alt-F3...it's just hanging on apt-get install [grub|lilo] command.

In rescue mode, when I get to a shell and mount the ubuntu parition, I can't install grub or lilo...as it prompts for the CD (*which is in the drive*)...looking at /etc/apt/sources.list shows why it is looking for the CD...but why can't I install through the internet (since the NIC is identified and setup)?  Every route I take, I hit a wall.

---

### Post by ZAxisMapping on 2006-03-30
I read in another thread to try using ReiserFS instead of ext3.  To my surprise....that actually worked!!

But my question is, do I really want to be using ReiserFS?  Everything I work under is ext3, and I'll need to transfer a bunch of files between the two different filesystems.  My impression is that ReiserFS is now a little out of date.

---

### Post by ZAxisMapping on 2006-03-30
Before getting too comfortable with ReiserFS, I tried one last different approach.  The following worked perfectly for me:


[http://ubuntuforums.org/showthread.php?t=66160&highlight=grub+hangs+installing]("http://ubuntuforums.org/showthread.php?t=66160&highlight=grub+hangs+installing")


1.  Reversed the boot order of my two SATA drives in BIOS.
2.  Installed Ubuntu to /dev/sdb (and grub had no issues)
3.  Switched back boot order in BIOS.

As best I can tell, the system boots off of the MBR on /dev/hda, as desired.

---

