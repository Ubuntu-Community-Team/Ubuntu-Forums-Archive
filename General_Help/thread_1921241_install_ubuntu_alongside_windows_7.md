---
title: "install ubuntu alongside windows 7"
date: 2012-02-06
forum: General Help
---

### Post by restricted on 2012-02-06
im trying to install ubuntu 11.10 x64 on my laptop but if i follow the default installation steps it does not recognize the windows 7 (im only able to erase the entire disk)
i switched to try mode and when im typing on terminal 
sudo fdisk -l
it shows the partition which i have 
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  3907026943  1953410048    7  HPFS/NTFS/exFAT
when im opening the gparted it does not find any partition
please tell me what i have to do (and always remember am in try mode )
for creating a new partition for ubuntu without causing problems to my windows system

---

### Post by mikejonesey on 2012-02-06
shrink the windows partition from the windows partition first, then use this "unallocated disk space"... :)

---

### Post by philinux on 2012-02-06
> **mikejonesey said:**
> shrink the windows partition from the windows partition first, then use this "unallocated disk space"... :)

+1  But defrag windows first.

---

### Post by Mark Phelps on 2012-02-06
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by Rebelli0us on 2012-02-06
You could leave your w7 as is,  go to Ubuntu software centrer and install Oracle VirtualBox, then run Ubuntu as a virtual machine from inside w7. The advantages -- you can run both OSes simultaneously and you don't have to risk your installation by screwing with the partitions. I'm running W7 virtual machine inside Ubuntu, works very well.

---

### Post by xyzzyman on 2012-02-06
> **Rebelli0us said:**
> You could leave your w7 as is,  go to Ubuntu software centrer and install Oracle VirtualBox, then run Ubuntu as a virtual machine from inside w7. The advantages -- you can run both OSes simultaneously and you don't have to risk your installation by screwing with the partitions. I'm running W7 virtual machine inside Ubuntu, works very well.

I think you may have written that wrong... You're getting into some Inception type stuff right there. You can't go to Ubuntu software center inside of an installation that doesn't exist yet. :)

Also @restricted, before messing with your partitions, make sure you have current backups of any important data, and you've burned any Windows recovery disks for your system.

---

### Post by Rebelli0us on 2012-02-06
> **xyzzyman said:**
> I think you may have written that wrong... You're getting into some Inception type stuff right there. You can't go to Ubuntu software center inside of an installation that doesn't exist yet. :)

Also @restricted, before messing with your partitions, make sure you have current backups of any important data, and you've burned any Windows recovery disks for your system.

lol, good catch. He has to dowload VirtualBox for Windoz, free from Oracle's website. Ubie works fine in VM and no risk involved.

---

