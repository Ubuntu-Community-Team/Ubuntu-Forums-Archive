---
title: "How do I save XP to a disk on Netbook ?"
date: 2010-02-07
forum: General Help
---

### Post by mrpenguin on 2010-02-07
I have a Asus Netbook that came with Windows xp already installed, I want to format my hard drive and install Ubuntu and not dual boot with windows but I would like to save windows xp thats on my netbook to a disk just in case I do decide later to switch back to windows ... can anybody tell me how I can do that ?

---

### Post by akashiraffee on 2010-02-07
If your netbook did not come with a disk to reinstall windows with, do not remove it from the drive!  You cannot make such a disk.

If it did come with one, don't worry about it.  Just back up your own files.

---

### Post by MelDJ on 2010-02-07
your laptop should have come with a xp restore disc. if not, don't remove it

---

### Post by mrpenguin on 2010-02-07
Its a Netbook, it dont have a dvd drive so it didnt come with the cd ... it was pre install on the hard drive

---

### Post by theozzlives on 2010-02-07
> **mrpenguin said:**
> Its a Netbook, it dont have a dvd drive so it didnt come with the cd ... it was pre install on the hard drive

It should've come with a recovery partition. Just leave that partition alone.

---

### Post by mrpenguin on 2010-02-07
> **theozzlives said:**
> It should've come with a recovery partition. Just leave that partition alone.


Will it show as a recovery partition when I install ubuntu ?

---

### Post by bumanie on 2010-02-07
It is best to choose manual at the partitioning stage to ensure that you don't touch the restore partition - as long as you don't do any operations on that, it should be fine. [Here's]("http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide") a page that explains manual partitioning. By the way, you can make clone of a hard drive by using dd commands, but as you sound fairly new to linux, it would not be advised. I think gparted live cd will also copy a partition from one drive/partition to another - go here for a run down on gparted and its uses. Don't attempt these operations unless you are comfortable that you fully understand the procedures first.

---

