---
title: "mount: special device dev/scd0 does not exist"
date: 2009-11-10
forum: General Help
---

### Post by vorbroker on 2009-11-10
"mount: special device dev/scd0 does not exist" error shows up when i click on the cdrom0 under the places tab. I'm new to linux and have no idea what that means or how to fix it. I searched the forums and couldnt find anything thats the same problem and has been resolved. I'm new to this and dont know many obvious fixes. I do know that im running 9.10 on a Lenovo Ideapad Y710 and the CD drive does work. I can boot from an install CD but after its installed it won't recognise the drive Thanks for the help. I usually resopnd quickly

---

### Post by mc4man on 2009-11-10
Could you run this in a terminal and see if your cdrom drive shows up

```
sudo lshw -C disk
```

Some models of  Lenovo have a history not being detected from the installed Os.

---

### Post by vorbroker on 2009-11-10
*-disk                       
       description: ATA Disk
       product: Hitachi HTS54252
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: BBFO
       serial: 080511BB2F00WDJ495VA
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=78744461
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=b9121dd9
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdc
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=39bd121c
  *-disk       
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdd


The last one is the only one i dont recognize...is that a CD drive?

---

### Post by mc4man on 2009-11-10
> The last one is the only one i dont recognize...is that a CD drive?doesn't appear to be. (*-cdrom: description is expected

could you run this and post, plus a quick description of your hardware ( internal drives, did you have any external drives, flash cards ect. connected when you ran the lshw? 

Are you single or dual booting?

```
sudo fdisk -l
```

Am going to assume now that only a boot disk works in drive ..?

---

### Post by vorbroker on 2009-11-10
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78744461

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952   17  Hidden HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9121dd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39bd121c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4661    37439451   83  Linux
/dev/sdc2            4662        4866     1646662+   5  Extended
/dev/sdc5            4662        4866     1646631   82  Linux swap / Solaris




I have an internal 250 GB hard drive that has windows 7 on it....but i think i messed it up...i cant boot windows at all and i also cant make a windows CD either because my CD drive is messed up haha

I also have a 320 GB external hard drive that is just for storing my movies picture music....

finally..I have a 40 GB umm...external hard drive that is running karmic..this is a hard drive from an old desktop i though I would play around with ubuntu on and not have to use any of my internal space....its connected to my laptop with a  "USB2.0 IDE & SATA cable"

i also might have had my motorola droid plugged in too when i ran the lshw im not sure

i only have ubuntu running right now and yes, only a boot disk works in the drive

---

### Post by mc4man on 2009-11-11
well there was a thread last year where a Lenovo laptop was displaying the same error message and same behavior as your's.

In that case everything was tried - bios changes, boot kernel options, ect.

The only solution that worked was to switch the bootloader from grub to lilo which was successful.

In your case, while lilo could be the answer, there are too many other potential factors, the least of which is karmic uses grub2 and I'm unsure as to if lilo would work as expected.
Also you have an 'odd' setup, your cdrom doesn't work in windows either and you have windows7 to boot.

I think you should first get the drive working in windows before anything else. 
( maybe do a search on cdrom high and low filters ( was an issue for some in vista, maybe also win7..?

---

