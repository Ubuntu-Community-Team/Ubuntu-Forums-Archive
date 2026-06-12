---
title: "Making USB stick Bootable"
date: 2009-11-02
forum: General Help
---

### Post by DigitalDisease666 on 2009-11-02
I need some help to make an 8GB USB Stick to boot Windows XP. I've been searching on google for last 2 days and couldn't find anythin'. I've tried with UNetBootin but it was useless.

---

### Post by P4man on 2009-11-02
Try another stick.
Or check if you dont have a [u3 enabled stick.]("http://en.wikipedia.org/wiki/U3") If you do you have to remove the U3 firmware.

edit: oh, I misread. to boot XP? No clue...

---

### Post by utnubuuser on 2009-11-02
and make sure it (the partitions), have a 'bootable' flag.  System>>Administration>>Partition Editor>>right-click partition>>Manage Flags>>select 'bootable'

---

### Post by FallenArms on 2009-11-03
Bumping this because I have the same exact issue.  The only partition on the drive is marked bootable, but I know there has to be some file included on the drive itself in order for the BIOS to recognize it as a bootable drive.  I could easily do this if I was in Windows, but I can't find any help on it in Ubuntu.

A summary of the issue is this: I have an .ISO installer file for Windows XP, which I want to load onto my flash drive and use to install Windows XP on my computer.

---

