---
title: "GRUB issue- want rid of it."
date: 2010-02-23
forum: General Help
---

### Post by geggs on 2010-02-23
Hi,
Im new to Linux, installed Ubuntu but following upgrades it would not boot but went into a GRUB console with 4 choices Boot ubuntu, recover ubuntu, memtest 86, memtest 86..something else..?

I dont know what to do with this so i plugged the SATA disk from PC 1 into PC2 via USB convertor cable and deleted the primary partition from the sata disk (PC1).  Im trying to get back to just having a disk with nothing on it. The disk is brand new and I want to install XP and ubuntu on it. (Or maybe just XP!!).
When I turn on PC 1 now I currently get a GRUB loading error, GRUB rescue message.
I'd like to get rid of GRUB altogether and just boot ubuntu from a CD again.

Help...
ta
Geggs the n00b

---

### Post by Bob535 on 2010-02-23
Insert XP Disc, go into your BIOS and make sure your CD drive is your primary boot. 

XP Setup should pop up when you turn the computer on.

Install XP.

After installing XP, take out the disc and put the ubuntu disc in.

Repeat the same steps above.

Now when you boot your machine it should show in Grub (which you need) the options for both XP and Ubuntu.

---

### Post by geggs on 2010-02-23
> **Bob535 said:**
> Insert XP Disc, go into your BIOS and make sure your CD drive is your primary boot. 

XP Setup should pop up when you turn the computer on.

Install XP.

After installing XP, take out the disc and put the ubuntu disc in.

Repeat the same steps above.

Now when you boot your machine it should show in Grub (which you need) the options for both XP and Ubuntu.

Hi my bootable XP disk is at work but I tried a win98 disk and I have changed the boot order to be CD first and ive disabled the 2 boot device. It still wont boot from the 98 disk and still comes up with GRUB message?  Frustrating! I have a non bootable copy of a XP disk here, if use my sata to USB convertor can I copy the XP CD files disk onto the disk then tranfer the HDD back to the original box and run it somehow? Im off sick so cant get the proper XP disk from work. Any advice appreciated!

---

### Post by uncle-c on 2010-02-23
Hi,
GRUB is still in your MBR. One of the ways to get rid of it is to boot up using a live CD. Once this is up and running fire up a konsole or terminal
and use the dd command to delete it :

```


$ dd if=/dev/zero of=/dev/sda count=1 bs=446 
```

(change sda to your own appropriate disk) 

this deletes all in the MBR except the partition table.

OR if you have a win 98 boot floppy lying around or can download it, boot up and from the command prompt run fdisk /mbr which re-writes the boot record.

To install XP from a CD which is not bootable there are plenty of methods: here are a few ( i haven't tried them though !)

How to obtain XP setup floppy disks

[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

Installing windows from a non bootable drive

[http://forums.techarena.in/windows-xp-support/722266.htm](http://forums.techarena.in/windows-xp-support/722266.htm)

[http://webolio.wordpress.com/2007/03/20/installing-windows-xp-using-a-non-bootable-cd-and-no-floppy-disks/](http://webolio.wordpress.com/2007/03/20/installing-windows-xp-using-a-non-bootable-cd-and-no-floppy-disks/)

Just do a google search you will find plenty of alternate methods.


HTH

---

### Post by geggs on 2010-02-24
> **uncle-c said:**
> Hi,
GRUB is still in your MBR. One of the ways to get rid of it is to boot up using a live CD. Once this is up and running fire up a konsole or terminal
and use the dd command to delete it :

```


$ dd if=/dev/zero of=/dev/sda count=1 bs=446 
```(change sda to your own appropriate disk) 

this deletes all in the MBR except the partition table.

OR if you have a win 98 boot floppy lying around or can download it, boot up and from the command prompt run fdisk /mbr which re-writes the boot record.

To install XP from a CD which is not bootable there are plenty of methods: here are a few ( i haven't tried them though !)

How to obtain XP setup floppy disks

[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

Installing windows from a non bootable drive

[http://forums.techarena.in/windows-xp-support/722266.htm](http://forums.techarena.in/windows-xp-support/722266.htm)

[http://webolio.wordpress.com/2007/03/20/installing-windows-xp-using-a-non-bootable-cd-and-no-floppy-disks/](http://webolio.wordpress.com/2007/03/20/installing-windows-xp-using-a-non-bootable-cd-and-no-floppy-disks/)

Just do a google search you will find plenty of alternate methods.


HTH

I cant get it to bbot up from my live CD or win98 CD or bootable DOS 7 it just goes into GRUB recovery every time.  Ive set the bios to boot from CD so I dont know what else to do.  Looks like i'll need to go up the attic and find some floppies! ARGG
I might try pluggin the disk into another PC and formatting it? Would that wipe the MBR??

---

### Post by uncle-c on 2010-02-24
[http://www.bootdisk.com/]("http://www.bootdisk.com/")

Will point to into the direction of creating a win98 boot floppy.Create the boot disk and make sure your BIOS  is set to "BOOT FROM FLOPPY" Once you get a command prompt issue the fdisk /mbr command and this should delete the grub in your MBR.
Alternatively download the XP setup floppy images  from the same site. Then boot up from these and install the XP from the non-bootbale XP Disk that you have. The installation will overwrite GRUB and you should have a working XP OS. You can then install  Ubuntu on a separate partition and this will overwite the windows bootloader with grub during the linux install but once completed it will present you with a menu to boot into  either of the two OS.

---

### Post by geggs on 2010-02-24
> **geggs said:**
> I cant get it to bbot up from my live CD or win98 CD or bootable DOS 7 it just goes into GRUB recovery every time.  Ive set the bios to boot from CD so I dont know what else to do.  Looks like i'll need to go up the attic and find some floppies! ARGG
I might try pluggin the disk into another PC and formatting it? Would that wipe the MBR??

The disk from the PC had 2 partitions so i deleted them to make 1 partition which i then formatted.  GRUB is gone and I can now boot from CD- found a OEM installation CD for XP
which is installing OK. Looks like the worst is over.
Thanks for those that offered advice.
Cheers
Geggs

---

