---
title: "hosed fstab - won't boot"
date: 2009-11-15
forum: General Help
---

### Post by scotc on 2009-11-15
Dear Ubuntu lads and lasses,
in trying to move my /home to a separate partition I find that I can't boot Ubuntu.
I think I damaged the fstab.

I have tried both live CD and Recovery Mode boot, but when I try to restore from fstab.bak (or to edit the fstab), I get the error message that the system drive is read-only (in recovery mode) or that I don't have access permission (in live CD).

How can I gain access to the system drive to correct any errors?

I think the error in the fstab is "errors =remount-**rw**", which I changed from "**ro**" because I thought it was wrong.

Alternatively, the problem might be the /home directory.  I THINK the original is still in the file system, with a COPY in the new location, but I can't be completely sure that is what I am seeing.

Help appreciated, Scot

---

### Post by sisco311 on 2009-11-15
Boot the  Live CD, open GParted(System -> Administration -> GParted) and check the partitions for errors(unmount, right click *Check*).

---

### Post by scotc on 2009-11-15
Tried that Sisco,
gparted found no errors.
Ubuntu still won't boot
Scot

---

### Post by scotc on 2009-11-16
bump

---

### Post by scotc on 2009-11-16
Dear all, I recovered the system so here it is for those who follow in my footsteps into the wilderness.

The Fstab was hosed, probably by removing the windows Sda1 drive, which according to Gparted is flagged as "boot".  I suspect that removing it meant that linux on sda2 could not boot because some part of grub /mbr was on the windows drive.

Trying to edit the fstab was a waste of time because Recovery Mode and Live CD found the drive to be read only.

I realised that I did have a way to read the drive - from windows via ext2fs programme, which for those that don't know is a wee prog that allows Windows to read and write to an ext2 drive i.e. a linux file system.  I use ext2fs to read the 3rd partition (shared) where all the docs created in windows and linux reside.

I knew it would override any permissions.

By my own default, windows would not mount the linux drive, so as usual I hadn't seen it when scrabbling around in windows trying to problem solve.

I simply gave the linux os drive a letter (z:) via the wee programme, then I could enter it and tweak the fstab with Textpad.

Sorted.

---

