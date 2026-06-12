---
title: "Does  Ubuntu re-installation help with dual boot?"
date: 2009-11-16
forum: General Help
---

### Post by rutiezer on 2009-11-16
The computer dual boots Ubuntu 8.04 and Windows XP, each on a separate drive.

Need to reinstall Ubuntu. Can't use Ubuntu to determine this -- can start Ubuntu only in recovery mode (which is not able to recover) and can get "limited" command line.

Can the installation process determine where was last installed? 
Want to reinstall Ubuntu on the same hard drive as was used in the prior Ubuntu installation.
Don't want to write over the Windows drive.

Does the installation process determine there is another operating system on one of the drives?

Does installation process lead one through setting up dual boot?

From Windows see only one drive, Local Disk labeled "D:", not "C:". Don't know why drives labeled this way. Don't see the drive containing Ubuntu. Can see "E:", DVD, "F:", DVD/CD, removable drives "G:" through "J:". Maybe it is on the not-visible drive "C:" See "A:", the floppy, but no "B:".
 

  

Thanks.

---

### Post by plusnplus on 2009-11-16
Can the installation process determine where was last installed?
>>> can, just carefully look the partition bar. mostly anything beside fat32/ NTFS, is linux partition (file sys and swap)

Does the installation process determine there is another operating system on one of the drives?
>>> it(the instalation) will do it automaticly

Does installation process lead one through setting up dual boot?
>>> yes

anyway, if you not confidence, backup first any data in your windows partition

---

### Post by JoelOl75 on 2009-11-16
I wouldn't use the "automatic" or "smart" install as it will leave the old 8.04 distro installed, and probably resize your windows partition to make room for 9.10 which is not what you want.

Just goto manual in the partition setup and pick your ext3 partition and set it to format as ext4 and set the mount point as '/' and make sure you have a swap partition. You can either go with the ubuntu way of creating an extended partition for swap and it will be named sdb5 or I usually just make it a primary partition (sdb2)  It would have been created when you installed 8.04 so it should be sdb5... It doesn't matter, just make sure you have one of adequate size (I make mine slightly bigger than my installed RAM or 3Gb, whichever is larger... although many have varying opinions on this).  Make sure to leave your NTFS partition (or FAT32 if you used it...) alone and all should install well, I should detect your windows install, and will probably write grub to the first drive (Which may be your windows drive) but I can't tell from the information you provided.

I hope this is of some help.

The problem with letting the partitioner 'do its thing' is that it will keep your old linux install.

The worst case senario would be for grub to not add windows to the menu, or grub to break and lock you out of windows. This shouldn't happen...but can be fixed by booting off the windows install cd, pressing "R" for recovery console and logging into your windows install and typing fixboot and/or fixmbr to wipe grub completly off the MBR.  This of course will lock you out of linux then.  This technique only works with 2000/XP. I think there's a different way for Vista and Win 7...  Just make sure not to format the NTFS partition and you should be OK, but backup just to be safe.  Sorry for the scary info...


The partitions should look similar to:

sda1    NTFS
sdb1    ext3
sdb5    swap

Just pick the ext3 partition and set it's mount point to "/" and might as well use the new ext4 filesystem if you wish (Or keep ext3)

This assumes the 2nd hard drive is the linux hard drive. If it's not, the sda and sdb will be reversed.  

Hope this helps

---

### Post by rutiezer on 2009-11-17
Thanks for information.


Don't have an installation CD for Windows XP although I do have the installation key. Lost it and other software installation CDs in moving.

When I start the Ubuntu installation with the 8.04 installation disk would it be better or possible to disconnect the data or power cable for the drive Windows is installed on after the grub has asked which operating system to start so that Ubuntu can't do anything to the Windows drive?

---

### Post by JoelOl75 on 2009-11-18
> **rutiezer said:**
> Thanks for information.


Don't have an installation CD for Windows XP although I do have the installation key. Lost it and other software installation CDs in moving.

When I start the Ubuntu installation with the 8.04 installation disk would it be better or possible to disconnect the data or power cable for the drive Windows is installed on after the grub has asked which operating system to start so that Ubuntu can't do anything to the Windows drive?
Probably not a good idea as ubuntu needs to write grubs MBR to the first bootable drive (the XP drive) and if it's not connected it will write it to the second drives MBR, so reconnecting the first drive will then boot the old MBR.

---

### Post by rutiezer on 2009-11-18
"Make sure to leave your NTFS partition (or FAT32 if you used it...) alone and all should install well, I should detect your windows install, and will probably write grub to the first drive (Which may be your windows drive) but I can't tell from the information you provided."

"Probably not a good idea as ubuntu needs to write grubs MBR to the first bootable drive (the XP drive) and if it's not connected it will write it to the second drives MBR, so reconnecting the first drive will then boot the old MBR."

What additional information is needed?
Don't want to lose the ability to dual boot to the Windows XP disk in installing Ubuntu 8.04, and, as I mentioned don't have installation disks but have key.

Is there a way to ensure Ubuntu installation does not write on disk containing Windows?
This is why I asked about disconnecting the Windows drive.

What determines the first and second bootable drives?
Don't see now in the BIOS the boot order.
Assume BIOS points to Ubuntu drive now, otherwise Ubuntu would not start booting and give the choice of Ubuntu or Windows XP.

---

### Post by JoelOl75 on 2009-11-24
It would be the order on the bus that determines boot order for BIOS that just simply lists "Hard Drive"

Seriously though, as long as you don't touch the NTFS/FAT partitions Ubuntu will (really shouldn't) break it.  If for some reason the Windows partition doesn't list in the grub menu it can be added in later..  Many people who install Ubuntu and somehow break grub by their own fault (By thinking they are being smart and removing the Win drive or something before Ubuntu install) and then freaking out and wiping the Linux partitions (Thinking this will fix the Windows problem, but now makes it worse as grub needs the /boot directory)

It will get it right, just don't mess with the NTFS partition.

---

