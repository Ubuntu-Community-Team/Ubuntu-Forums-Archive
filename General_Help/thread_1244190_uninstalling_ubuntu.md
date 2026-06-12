---
title: "uninstalling ubuntu"
date: 2009-08-19
forum: General Help
---

### Post by TwistedGhost on 2009-08-19
so i love ubuntu but its just not what i need for what i am trying to use my computer for so i want to switch back to windows

i have a compaq presario sr1303wm
i have a windows xp home edition disk when i put it in and boot my computer it starts up and it loads the installer
when it gets to the partition area it says that i only have 1 partition and it only has like 235 mb when i have a 250gb hardrive
i dont know what to do or how to do it please help

---

### Post by kestrel1 on 2009-08-19
> **TwistedGhost said:**
> so i love ubuntu but its just not what i need for what i am trying to use my computer for so i want to switch back to windows

i have a compaq presario sr1303wm
i have a windows xp home edition disk when i put it in and boot my computer it starts up and it loads the installer
when it gets to the partition area it says that i only have 1 partition and it only has like 235 mb when i have a 250gb hardrive
i dont know what to do or how to do it please help
Use the Ubuntu live CD & then use gparted to sort out your partitions or download the gparted live CD & use that instead.

---

### Post by moody_mark on 2009-08-19
Isnt there an option in the windows installer the install and delete the existing partitions? I thought there was, oddly I remember the "L" key being used to confirm partition deletion, thats why it sticks in my mind.

---

### Post by buffy^ on 2009-08-19
I would guess that the windows intaller might not be seeing the swap partition.

Your other option is to download the tools form the HDD manufacture and repartition the disk.


You may also wish to try: 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by acron1 on 2009-08-19
As Kestel1 said gparted is the easiest option. You can also download and burn a live cd [URL="http://sourceforge.net/projects/gparted/files/gparted-live-stable/"]here
[/URL] burn the .iso and boot with it in the drive. Once booted you can delete and/or edit and format any partitions.
Good luck

---

### Post by kestrel1 on 2009-08-19
> **moody_mark said:**
> Isnt there an option in the windows installer the install and delete the existing partitions? I thought there was, oddly I remember the "L" key being used to confirm partition deletion, thats why it sticks in my mind.
Yes you are correct that you should be able to delete partitions under the windows installer, but unfortunately the windows installer will not see linux partitions & therefore you have a problem. Gparted is the best option.

---

### Post by TwistedGhost on 2009-08-19
like you said windows will not detect the linux partitions
i am trying the gparted live cd and will get back to you thanxs for all your help

---

### Post by TwistedGhost on 2009-08-19
ok so i used the gparted live cd and deleted the partition but the windows cd still will not detect the hardrive

and since i deleted the partition i no longer can even boot my computer

please help i just want to get back to windows

---

### Post by acron1 on 2009-08-19
OK that's no problem boot again with the gparted cd an format the drive in 1 continuous partition using the NTFS file format (you can also use FAT32 as your 2nd best option). Once that's done Windows will be able to see your drive UNLESS you are trying to install XP and have a SATA HDD as XP did not natively come with SATA drivers. If you have a SATA HDD look [URL="http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/"]at this little bit.
[/URL]

---

### Post by wojox on 2009-08-19
Google Killdisk download it and burn it to a cd. It will wipe the drive clean. I use it all the time.

---

### Post by kestrel1 on 2009-08-20
> **acron1 said:**
> OK that's no problem boot again with the gparted cd an format the drive in 1 continuous partition using the NTFS file format (you can also use FAT32 as your 2nd best option). Once that's done Windows will be able to see your drive UNLESS you are trying to install XP and have a SATA HDD as XP did not natively come with SATA drivers. If you have a SATA HDD look [URL="http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/"]at this little bit.
[/URL]
I would suspect that it could be a SATA drive & XP does not have drivers for any SATA controllers. If you enter the BIOS you should be able to set the drive to look like an IDE HDD to the XP installer, therefore it should be recognised.

---

### Post by acron1 on 2009-08-20
Wow I did not now that. CooL!

---

### Post by kestrel1 on 2009-08-20
> **acron1 said:**
> Wow I did not now that. CooL!

Not sure if all machines have this built in to the BIOS but the ones with SATA drive that I have worked on do. The actual wording in the BIOS will be different, but it should be pretty straight forward to find.

---

### Post by TwistedGhost on 2009-08-22
so the computer that i am using doesnt have that option how can i tell if my hdd is sata or ide?

---

### Post by ks07 on 2009-08-22
> **TwistedGhost said:**
> so the computer that i am using doesnt have that option how can i tell if my hdd is sata or ide?
Two options:
1) From the Ubuntu Live CD, open a terminal and run
```
sudo fdisk -l
```You should get an output that looks similar to this: 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88fac4ac

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   *           1       18740   150529018+   7  HPFS/NTFS
**/dev/sda2**           18741       19457     5759302+  1c  Hidden W95 FAT32 (LBA)
```The bits in bold are what we are interested in. If it says 'sda' then you have a SATA drive. If it says 'hda' then you have an IDE drive.

2)Otherwise, open your computer and look at the cable coming out of the back of your hard disk drive. (!Careful leaving it on while opening it!) If it's thin and red, it is SATA. If it's wide like a ribbon, it's IDE.

[See this picture: IDE and SATA]("http://www.computer-hardware-explained.com/image-files/sata-vs-ide-labelled.jpg")

---

### Post by kestrel1 on 2009-08-23
> **ks07 said:**
> Two options:
1) From the Ubuntu Live CD, open a terminal and run
```
sudo fdisk -l
```You should get an output that looks similar to this: 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88fac4ac

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**   *           1       18740   150529018+   7  HPFS/NTFS
**/dev/sda2**           18741       19457     5759302+  1c  Hidden W95 FAT32 (LBA)
```The bits in bold are what we are interested in. If it says 'sda' then you have a SATA drive. If it says 'hda' then you have an IDE drive.

2)Otherwise, open your computer and look at the cable coming out of the back of your hard disk drive. (!Careful leaving it on while opening it!) If it's thin and red, it is SATA. If it's wide like a ribbon, it's IDE.

[See this picture: IDE and SATA]("http://www.computer-hardware-explained.com/image-files/sata-vs-ide-labelled.jpg")

Using the command above does not show if you have SATA or IDE.
I have two IDE & one SATA drive. They all show as SD* & not HD* Can't remember the the reason for SD* & HD*, but it is not dependent on drive type. The best way is to open the case, but always unplug the mains before doing so.

---

### Post by egalvan on 2009-08-23
> **kestrel1 said:**
> Using the command above does not show if you have SATA or IDE.
I have two IDE & one SATA drive. **They all show as SD* & not HD* **Can't remember the the reason for SD* & HD*, but it is not dependent on drive type. The best way is to open the case, but always unplug the mains before doing so.

The driver code was changed, merging serial-based (SCSI) and parallel-based (IDE PATA).

So all drives are now sd

---

### Post by kestrel1 on 2009-08-23
> **egalvan said:**
> The driver code was changed, merging serial-based (SCSI) and parallel-based (IDE PATA).

So all drives are now sd
I knew there was a simple explanation. Thanks egalvan.

---

### Post by egalvan on 2009-08-23
> **TwistedGhost said:**
> 

i have a compaq presario sr1303wm

it says that i only have 1 partition and it only has like **235mb** when i have a **250gb** hardrive
i dont know what to do or how to do it please help

The fact that the XP installer sees SOMETHING says that it's not a SATA issue... it would show NO drives/partitions at all if it were a SATA issue.

I am looking at the 235MB stated size... are you SURE that that is MEGAbytes?

235Gb is the approximate size for a 250GB drive... so maybe you misread it?

And all the XP install CD's that I have ever used had an option to choose partitions, and to delete and create partitions.


Really, GRUB is a most well-mannered beast, and the *.nix instllers tend to be friendly as well...
so I don't think they munged the drive.

I would download Darik's Boot And Nuke

dban.org

it's small... under 10MB download...
and for a single-drive system that needs the WHOLE drive erased, it is easy to use.
I have used it, and can recommend it.

KillDisk is  another one, but I have no experience with this.

---

### Post by ks07 on 2009-08-23
> **kestrel1 said:**
> Using the command above does not show if you have SATA or IDE.
I have two IDE & one SATA drive. They all show as SD* & not HD* Can't remember the the reason for SD* & HD*, but it is not dependent on drive type. The best way is to open the case, but always unplug the mains before doing so.

> **egalvan said:**
> The driver code was changed, merging serial-based (SCSI) and parallel-based (IDE PATA).

So all drives are now sd

Ah I thought I was being smart for a second then. Oh well thanks for telling me. :)

---

### Post by egalvan on 2009-08-23
> **ks07 said:**
> Ah I thought I was being smart for a second then. Oh well thanks for telling me. :)

Just to make sure, I was talking about the CODE, not the DRIVE :)

Opening the case and looking at the hardware is a sure way of telling what kind of drive it is.

At times, the BIOS can also shed light on this.

---

### Post by TwistedGhost on 2009-09-09
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b291

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23947   192354246   83  Linux
/dev/sda2           23948       24321     3004155    5  Extended
/dev/sda5           23948       24321     3004123+  82  Linux swap / Solaris


it is a sata drive and what it is is a have a 200gb harddrive that anytime i try to install windows windows will not even detect the ubuntu partition

---

