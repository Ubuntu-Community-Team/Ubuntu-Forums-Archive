---
title: "Get files from wubi"
date: 2010-10-22
forum: General Help
---

### Post by krytorii on 2010-10-22
Hey guys, this is probably really noobish but I need to recover some files but my computer is pretty much dead.

Windows XP spontaneously shuts down whilst booting and wubi goes into grub.

I dont care too much for recovering windows, I backed up the important files (photos and the like). I was gonna upgrade to 7 next week anyway.

What I need to do is get a few files from wubi.

I managed to get my windows files from a live cd and copy them to a pen drive. Alot of my wubi ones are on ubuntu one so theyre safe, but some folders were too large so I hadnt backed them up.

Where are the wubi files located so I can copy them?

---

### Post by drs305 on 2010-10-22
You can access the files from the live cd by first mounting the windows partition and then the wubi root.disk: (Change the X,Y values to the windows partition).

Edited:
```
sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sd[COLOR="DarkRed"]XY[/COLOR] /mnt/windows
sudo mount **-o loop** /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
```

You can then access the wubi files with a browser.
```
nautilus /mnt/wubi
```

---

### Post by krytorii on 2010-10-22
it all worked up until 

sudo mount /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
[FONT=monospace]
Where it said:

mount: /mnt/windows/ubuntu/disks/root.disk: can't read superblock

I switched the XY part of the 2nd line with "a2" (where my wondows and therefore wubi is)

[/FONT]

---

### Post by drs305 on 2010-10-22
My error. You have to loop mount it:
```
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
```
I'll change the original as well.

---

### Post by krytorii on 2010-10-22
[FONT=monospace]I tried that, and it comes back with

[/FONT]/mnt/windows/ubuntu/disks/root.disk: Input/output error

---

### Post by drs305 on 2010-10-22
OK, let me pull out my laptop with wubi and take a look.

---

### Post by drs305 on 2010-10-22
The commands work for me. See if your system finds the root.disk file in the location I indicated:

```
ls /mnt/windows/ubuntu/disks
```

Then if wubi is mounted:
```
ls /mnt/wubi
```

If it's not found, confirm your Windows install is on the device you mounted (sdXY). See if you can list the contents of windows at all, through either the command line or a browser:
```
ls /mnt/windows
```

Added: You might want to run all the commands fresh:
sudo umount /mnt/wubi
sudo umount /dev/sd[COLOR="DarkRed"]XY[/COLOR]
Then mount Windows & then Wubi.

It's possible you have two Windows partitions, a boot partition and a main partition. The root.disk file should be on the main Windows partition.

---

### Post by krytorii on 2010-10-22
It's not in that location, but it is the main/correct windows partition (all the normal folders are listed there).

---

### Post by drs305 on 2010-10-22
That's where the root.disk is installed on my laptops with the default settings. If you have windows mounted on /mnt/windows, you can run a search with this command:
```
find /mnt/windows -type f -iname root.disk
```

---

### Post by krytorii on 2010-10-22
I tried the search, there was no output/message/result.

---

### Post by drs305 on 2010-10-22
If you would like to run the boot info script perhaps it can shed some light:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Post the contents between "code" tags, which you generate with the # icon in the post's menubar.

---

### Post by krytorii on 2010-10-22
Sorry for not replying earlier.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,579,839    12,579,777   c W95 FAT32 (LBA)
/dev/sda2    *     12,579,840   390,700,799   378,120,960   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        4397-A934                              vfat       PRESARIO_RP                   
/dev/sda2        2478048764FEA31F                       ntfs       PRESARIO                      
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by drs305 on 2010-10-22
Unfortunately the script also didn't locate the root.disk file. The script did see the Windows files normally found in the same partition and some traces of a Wubi installation, such as 'C:\wubildr.mbr = "Ubuntu" '. But it did not find any wubi installation and most importantly the root.disk.

You were correct that the partition to mount was sda2. 

You could mount your other partitions and perform a search for root.disk as you did for the sda2 partition, just in case the file is elsewhere on the drive. The boot script doesn't look everywhere, so it *could* be somewhere else on the drive, but the chances aren't great.

There are apps such as PhotoRec and Test Disk that might do a better job of finding the file but I have limited experience with them in trying to find specific files. 

root.disk is the only filename I know that wubi uses. I wouldn't format the disk or erase any files in case someone else reads this thread and can provide some additional information or a different way of accessing your Ubuntu files, if they still exist.

---

### Post by krytorii on 2010-10-22
Ahh ok. Thank you for your help :)

---

