---
title: "I can't install Ubuntu. Four primary partitions."
date: 2012-02-07
forum: General Help
---

### Post by plasticcorndog on 2012-02-07
I have a dilemma.  This is what it looks like:
      [http://imageshack.us/photo/my-images/96/screenshotat20120207075.png/](http://imageshack.us/photo/my-images/96/screenshotat20120207075.png/)
      Any help would be so much appreciated.  Basically I have a dynamic  disk in Windows 7.  I want to run Ubuntu on this computer. Gparted is not  allowing me to create another partition, but suggests that I make an  extended partition... but it won't let me because every time I try to  make a partition it gives me that message.  I can't install ubuntu  because the installer deems my unallocated space as unusable.  I'm going  crazy I've spent so much time trying to do this.  Please help me out if  you can!  Most of this stuff is new to me so... please keep simple and I hope I haven't ruined anything through my impatience and not wanting to learn everything about partitions before installing this OS.

Thank you so much!

---

### Post by hadi2 on 2012-02-07
The error message explains it completely, You can't have more than 4 primary partitions and you already have four: /dev/sda1 /dev/sda2 /dev/sda3 and /dev/sda4 , The only solution would be to delete one primary partition and format it as an extended partition.

---

### Post by OGpmpdog on 2012-02-07
Hi,

The pic shows you already have 4 primary partitions...fyi...it's more flexible to have extended partitions, as primary partions cant be modified, only deleted.

Have you thought of how you will dual-boot? Should you decide to install GRUB to the MBR, GRUB may conflict with your Windows bootloader - and cause more frustration.

---

### Post by plucky on 2012-02-07
> **OGpmpdog said:**
> Hi,

The pic shows you already have 4 primary partitions...fyi...it's more flexible to have extended partitions, **as primary partions cant be modified, only deleted**.

Have you thought of how you will dual-boot? Should you decide to install GRUB to the MBR, GRUB may conflict with your Windows bootloader - and cause more frustration.

Not quite right.You cannot create more than 4 primary partitions,but you can resize them.

---

### Post by Mark Phelps on 2012-02-07
Plus ... Linux can't use Dymanic Disks ...

---

### Post by jasonrisenburg on 2012-02-07
It may not be waht you want but have you tried wubi or another type of virtual drive?

---

### Post by nipunshakya on 2012-02-07
> **plasticcorndog said:**
>   Basically I have a dynamic  disk in Windows 7.  I want to run Ubuntu on this computer.
Thank you so much![B]

Ubuntu cannot be installed in a dynamic disk[/B]. [B]
You cannot have more than 4 primary partitions.[/B]

If you have a windows 7 disk with you, i suggest you reinstall windows 7 with proper arrangement of partitions(with primary partitions) and then go for a ubuntu installation.

Refer to the following for dual boot
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

If you just want to install ubuntu anyway, u first extend your filesystem labeled 'Gateway' to make use of unallocated space.(use gparted, see [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html))

U also might want to convert your dynamic disks to basic ones before installing ubuntu
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)

Regarding partitions, see the following:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

Hope they help you out.

Regards,WinuxUser

---

