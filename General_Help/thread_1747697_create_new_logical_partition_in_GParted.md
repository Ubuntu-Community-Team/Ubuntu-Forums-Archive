---
title: "create new logical partition in GParted"
date: 2011-05-02
forum: General Help
---

### Post by DanBender on 2011-05-02
I'm trying to create a new logical partition on my Mythbuntu system so I can install a Windows XP virtual machine into it, with the hopes of eliminating my current dual-boot setup.

My current partition setup is:
```
sda1          NTFS, 30.00 GiB, current Windows installation
sda3          ext4, 28.61 GiB, /
sda4          extended, 38.15 GiB
     sda5     swap, 9.54 GiB
     sda6     ext4, 28.61 GiB, /home
[unallocated space], 383.80 GiB
sda2          ext4, 450.96 GiB, media disk
```If this list of partitions seems weird, it is. I'm going to migrate sda3-sda6 to a new hard drive once I find out if Windows on a VM will do what I want, or if I need to continue to dual-boot like I am now (I will also migrate either sda1 or the new sda7); I'd like to know this before I try to migrate disks; I only want to have to do it once.

Anyway, like I said at the top, I'd like to install a new partition to house the disk image for the Windows VM. I have enough partitions it needs to be a logical partition, so I'd like to place it in the unallocated space immediately after sda6. However, if I choose "New" in the GParted GUI, it says:
[QUOTE="GParted"][B]It is not possible to create more than 4 primary partitions
[/B] 
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.[/QUOTE]It then puts me back into the main window without giving me the option to create a *logical* partition. The resize/move option is also greyed out for the extended partition. I tried stopswap and unmounting sda6, but it won't unmount because the "disk is busy." Probably because it's /home. Is it possible to extend this like I describe during a normal session, or do I need to use GParted Live to do it?

---

### Post by ~Plue on 2011-05-02
You'll need to use the live cd to make changes to /home (and sda4) because when you're logged in as the normal user, the /home partition is in use. 
//And once the unallocated space is added to the extended partition, you should be able to create more logical volumes.

---

### Post by DanBender on 2011-05-12
Downloaded GParted Live and ran it off USB; solved now.

---

