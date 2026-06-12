---
title: "unable to boot!"
date: 2010-05-17
forum: General Help
---

### Post by ubunterooster on 2010-05-17
Something seemed odd so I tried to reboot. After several failures I have shrunk the partition so I can boot Knoppix. It gives an error when trying to mount sda1.

Edit: did I get "rm fs"ed? It's all I can think of.

---

### Post by oldfred on 2010-05-17
this will scan your system. Not sure if all the commands it wants are in knoppix. It will protest if it is missing something:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by ubunterooster on 2010-05-17
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: /dev/sda2 already mounted or sda2 busy

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003a705

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   153,597,464   153,595,417  83 Linux
/dev/sda2         153,597,465   245,971,214    92,373,750  83 Linux
/dev/sda3         245,971,215   250,067,789     4,096,575  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        369d5c4c-ba77-411c-ae52-dbd550db7ad4   ext4                                     
/dev/sda2        4cd46879-90af-4a7f-9f56-3bb81b7303c9   reiserfs   /                             
/dev/sda3        1a00cf8d-ce46-408d-8cc3-1cac8edfb6e7   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/root        /                        reiserfs   (rw,relatime)

=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
```[COLOR=Lime]Okay...now?[/COLOR]

---

### Post by oldfred on 2010-05-17
Do not know if theses work with reiserfs or not:

Finds superblock backups:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk - see other instructions for partition repairs also:
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---

### Post by ubunterooster on 2010-05-17
The reifers is fine; It's what is now in use. I'll try it on sda1 and report back.

---

### Post by ubunterooster on 2010-05-17
posted via PartedMagic: results of testdisk:


```
TestDisk 6.12-WIP, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0  32 33  9560 254 63  153595417
 1 * Linux                    0  32 33  9560 254 63  153595417
 2 P Linux                 9561   0  1 15310 254 63   92373750 [/]
 3 P Linux Swap           15311   0  1 15565 254 63    4096575











*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```

---

### Post by ubunterooster on 2010-05-17
Booting from sda1 now gives a "no root filesystem" error and hangs. I'll reinstall :-(

---

