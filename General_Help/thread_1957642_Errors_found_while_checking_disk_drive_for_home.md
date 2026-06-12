---
title: "Errors found while checking disk drive for /home"
date: 2012-04-12
forum: General Help
---

### Post by caray on 2012-04-12
After one inproper shutting-down, the error "**Errors found while checking disk drive for /home** " happens when I reboot PC. I wonder How to fix it?

---

### Post by LinuxFan999 on 2012-04-12
Does Ubuntu still boot despite the error message?

---

### Post by oldfred on 2012-04-13
If still having issues you might try e2fsck. You have to use liveCD so the partition is not mounted. Change example from sdb1 to whatever your /home is.

#From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by caray on 2012-04-13
Behind it, the message shows "Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery". If I choose "F", it takes several minutes to check the disk and then I can log in. But it will happen once I reboot the system again. I wonder how I can fix it once for all?

---

### Post by caray on 2012-04-13
Thanks for your reply. Well, I am not quite experienced with Ubuntu. To avoid ruinning it, can you give me more details on its recovery?
 
> **oldfred said:**
> If still having issues you might try e2fsck. You have to use liveCD so the partition is not mounted. Change example from sdb1 to whatever your /home is.
 
#From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by oldfred on 2012-04-13
When you reboot and it runs a filecheck it may not see anything & just boot. But sometimes the errors are still there. Running e2fsck from liveCD forces a full filecheck.

I you want more info from terminal run this (q to exit):
man e2fsck

---

### Post by caray on 2012-04-13
Thnaks for your reply. I created a USB stick for Ubuntu. When I boot my pc through USB, Installer boot menu shows several options as
Run Ubuntu from this USB
Install Ubuntu on a hard disk
Test memory
Boot from first hard disk
Advanced Options
Help
 
I wonder which one I should choose in order to run e2fsck you mentioned?
 
 
 
> **oldfred said:**
> When you reboot and it runs a filecheck it may not see anything & just boot. But sometimes the errors are still there. Running e2fsck from liveCD forces a full filecheck.
 
I you want more info from terminal run this (q to exit):
man e2fsck

---

### Post by caray on 2012-04-13
When I boot in by choosing "Run Ubuntu from this USB" and run "sudo e2fsck -C0 -p -f -v /dev/sdb1" in the terminal, it reports that "/dev/sdb1 is mounted. WARNING!!! the filesystem is mounted. If you continue you ***WILL*** casue SEVERE filesystem damage".
 
Anyway, please let me where I can run this command.

---

### Post by oldfred on 2012-04-13
Is sdb1 then the USB drive. Sometime the drives get reordered when you plug a drive in.

To see what drives and partitions you have 

sudo fdisk -lu

---

### Post by NikS on 2012-04-26
I konw this is not my thread, but just mentioning that this worked for me. Was facing the same issue, I went into the recovery console from GRUB menu.
There allowed it to scan. It mounted swap, and during scan listed drive that had issues.
selected to fix the issues manually by pressing m when it asked and executed the command above for the drives mentioned.
Now booted in without a problem..

Thanks guys! :)

---

