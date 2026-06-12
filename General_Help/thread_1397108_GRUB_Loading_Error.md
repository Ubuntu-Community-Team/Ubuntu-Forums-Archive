---
title: "GRUB Loading Error"
date: 2010-02-02
forum: General Help
---

### Post by gutierrezfam on 2010-02-02
I'm running the Netbook Remix version of Kubuntu 9.10 (dual boot with Windows XP on a separate partition).  I had not booted into Windows in over a month, but tried to yesterday (via GRUB menu).  I got some error from something other than GRUB saying that it couldn't find Windows and that it had to reinstall the OS and delete all data.  I said NO.  But ever since, I see the following:

"GRUB Loading"
"eror: no such partition"
"grub rescue>"

I've read a few other posts on this topic.  tried to access the full-up grub with a live-usb, but it doesn't have it, so I can't run some to the recommended commands.  

at the grub rescue> prompt, if I type "ls" I get: (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)

and if I type "set" I get: prefix=(hd0,6)/boot/grub
and root=hd0,6

I did manage to get this:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x845a4551

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,623,859    29,623,797   7 HPFS/NTFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4          29,623,860   182,723,309   153,099,450  1f Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7AE0A82DE0A7EE17                       ntfs                                     
/dev/sda2        CCED-990E                              vfat       PE                            
/dev/sdb         08BE-5862                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

```

I suspect that my original Linux partition was in /dev/sda4 (I noticed this when pretending to re-install ubuntu, on the "Prepare Partitions" step...  it just looks like the right size.

Can anyone please help?  Worst case, I really only need to retrieve ONE file from my "Documents" directory...  otherwise, I'm OK with doing a full re-install - but if I can avoid it, I'd like that.  Thanks.

---

### Post by theozzlives on 2010-02-02
If you can boot the live USB, you should be able to retrieve all important files.

---

### Post by gutierrezfam on 2010-02-03
With the Live USB, I can only see the ntfs partition (Windows XP) and the fat32 partition (my netbook's "recovery" partition) mounted.  It apparently doesn't "see" the linux partition.  

Assuming that my linux partition is sda4, could the problem be because the system doesn't know what the "filesystem type" is?  Where do I go from here?

---

### Post by john newbuntu on 2010-02-03
The boot info summary says that GRUB2 should be looking at sda6.  But your partition info looks messed up.  The partition table knows nothing about sda6.  Some of the filesystems do not even mount when forced.
Lookup for a utility called "testdisk".  You may need to correct your partitions first before you proceed.  Get a second opinion before you start anything.

---

### Post by Leppie on 2010-02-04
try accessing the drive using fdisk:
```
sudo fdisk /dev/sda
```if it prompts you that errors have been found and fdisk can try to correct those, let it do so.

if you do not remember how you partitioned your drive, testdisk could destroy your linux partition tables as it could recover them. however, installing testdisk also installs photorec which might be able to recover that one file you want back:
```
sudo apt-get install testdisk
sudo photorec
```NOTE: in order to be able to install testdisk, you need to enable the universe repository.

to start testdisk:
```
sudo testdisk
```
you will have the possibility to take a look at the contents of the partition you're trying to recover. so if you see that the partition you selected has the files you're looking for, you can try to have testdisk repair the partition table for that partition. obviously save the files you want to keep first using photorec.

---

