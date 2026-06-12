---
title: "How to determine the type of a filesystem drive?"
date: 2009-07-19
forum: General Help
---

### Post by elmichy on 2009-07-19
Hi everyone,

I managed to mount an external drive system by typing at the command line:


[CENTER][LEFT]sudo  mount   -t  vfat      /dev/sdv1     /media/mynewdrive
[/LEFT]
 

[LEFT]but, I did so by guessing the drive type as  [COLOR=DarkRed]vfat[/COLOR]. I  really did not found a 

 way to determine it. I tried using [COLOR=DarkRed]mount[COLOR=Black] and [COLOR=DarkRed]sudo fdisk -l [COLOR=Black]but, I don't get 

the type explicitly. Is there a way to find out?  [/COLOR][/COLOR][/COLOR][/COLOR]


thanks, :)

elmichy

 
[/LEFT]
[/CENTER]

---

### Post by Whiffle on 2009-07-19
You might be able to get it from:

sudo file -s /dev/sda1

where sda1 is the node of the device.

---

### Post by Sidewinder1 on 2009-07-19
First. WELCOME to Ubuntu Forums!!!
You seem to prefer CLI,; I avoid it (like many, former winbloze users) :-)
But I'll give you my GUI way:
Click on Places---->Home
In the left column right click on the Ext. HDD or any internal HDD that wasn't automatically mounted and in that menu click Mount. NOTE: if the Ext. HDD has two partitions (NTFS/FAT32 and ext3/ext4) you'll have to mount each separately using the process above.
Each drive (partition) should now have an icon on your Desktop. Right click it, then click Properties, then click Volume.
That should give you file system, mount point, UUID,...etc.
HTH,
Side

---

### Post by ibutho on 2009-07-19
One good tool is parted. Try 
```
parted -l
```
On my laptop I get the following output
```

Model: ATA WDC WD1600BEVS-6 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  104GB  104GB   primary   ntfs         boot 
 3      104GB   148GB  44.4GB  extended                    
 5      104GB   114GB  10.8GB  logical   ext3              
 6      114GB   115GB  535MB   logical   linux-swap        
 7      115GB   148GB  33.0GB  logical   ext3              
 2      148GB   160GB  12.1GB  primary   ntfs 
```

---

### Post by lswb on 2009-07-19
You can try a type of "auto" with the mount command and it will try to "guess" the correct filesystem.

sudo mount -t auto /dev/sdxx mountpoint

---

### Post by jerome1232 on 2009-07-19
Along with the above if you don't specify the type Ubuntu will guess for you.

```
mount /dev/sdx# /media/mount\ point
```

---

### Post by elmichy on 2009-07-19
Thanks everyone, :) I am learning  because of you people!!

I tried every option:

first, sudo file -s /dev/sda1

and it returned x86. I used it but, did not work.

Then, I tried the GUI approach but, Home did not show any HDD.

Then I used:   sudo parted -l, and the output was

fat32; once more, the drive was not mounted.

And finally, I let Ubuntu determine it automatically but, it asked me to specify it. 

I still don't get why mount only accepts [COLOR=DarkRed]vfat [COLOR=Black]as the correct argument. I know I was lucky but, 

I am not sure if I would be able to pull it off for other drive. 

Thanks, for the suggestions!!
[/COLOR][/COLOR]

---

### Post by ibutho on 2009-07-20
> 
I still don't get why mount only accepts vfat as the correct argument. I know I was lucky but, 
Vfat is whats used for various FAT partitions, so its the correct filesystem to use with the mount command.

---

### Post by elmichy on 2009-07-20
Thanks, it makes complete sense :).

---

