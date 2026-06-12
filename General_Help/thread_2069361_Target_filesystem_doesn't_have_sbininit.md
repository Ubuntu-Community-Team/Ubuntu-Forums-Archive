---
title: "Target filesystem doesn't have /sbin/init"
date: 2012-10-10
forum: General Help
---

### Post by GuidoGM on 2012-10-10
Hello everybody,

I have a problem. I couldn't mount my ubuntu partition, my windows partition is working ok. 

What I tried is use a live cd and mount the ubuntu partition and the message i got was:

Unable to mount 156GB Fylesystem 
Error mounting:mount: wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or oder error 
In some cases useful info is found syslog-try 
dmesg|tail or so

Besides when i want to use ubuntu, after the selected it on the grub this error appears :

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.
```


I've also used Boot info script and this was the result:

```
     Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================

 
=> Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
  
  1 of the same hard drive for core.img. core.img is at this location and 
    
looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed 
in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR 
of /dev/sdc.


sda1: __________________________________________________________________________

 
   File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    
Boot sector info:  No errors found in the Boot Parameter Block.
   
 Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________

  
File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
   
 Boot sector info:  No errors found in the Boot Parameter Block.

Operating System:  Windows 7
    Boot files:
        /bootmgr /Boot/BCD /Windows/System32/winload.
exe

sda3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown

    Boot sector info:
 

sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info:
 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,

       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so


sda6:
 __________________________________________________________________________

 
   File system:       swap
    Boot sector type:  -
    Boot sector info:
 

sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
 ........>..sr>........*.9...0...~.....~...f...M.f.f....f..0~....>E}.u......

    Boot sector info:  Syslinux looks at sector 2139032 of /dev/sdb1 for its 

                       second stage. SYSLINUX is installed in the  directory. 

                       No errors found in the Boot Parameter Block.

    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.
sys

sdc1: __________________________________________________________________________

 
   File system:       vfat
    Boot sector type:  Syslinux 4.00-4.02
    Boot sector info:
  Syslinux looks at sector 7279072 of /dev/sdc1 for its second stage. 
It is very unlikely that Syslinux is (still) installed. The second stage could not be 
   
found. No errors found in the Boot Parameter Block.
   
 Operating System:  
    Boot files:
        

============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders,
 total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical):
 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1
    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2 
          3,074,048   617,474,047   614,400,000   7 NTFS / exFAT / HPFS
/dev/sda3 
        617,476,094   976,773,119   359,297,026   5 Extended
/dev/sda5         617,476,096
   962,115,583   344,639,488  83 Linux
/dev/sda6         962,117,632   976,773,119 
   14,655,488  82 Linux swap / Solaris


Drive: 
sdb _____________________________________________________________________


Disk /dev/sdb: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 
948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size
 (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector   
 End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,915,775     3,915,744   b W95 FAT32


Drive: sdc
 _____________________________________________________________________


Disk /dev/sdc: 8006 MB, 8006926336 bytes
39 heads, 39 sectors/track, 10281 cylinders,
 total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical):
 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *  
        8,064    15,638,527    15,630,464   c W95 FAT32 (LBA)


"blkid" output:
 ________________________________________________________________

Device           UUID      
                             TYPE       LABEL

/dev/loop0                               
               squashfs   
/dev/sda1        9EA4D140A4D11B99                       ntfs     
  System
/dev/sda2        163003D93003BF2D                       ntfs       TI102977W0D
/dev/sda5  
      d9434996-7fc0-4872-8a36-1b9fde505402   ext4       
/dev/sda6        1a53123e-81e4-4dad-ac3b-1fa78dd3e012  
 swap       
/dev/sdb1        B079-C175                              vfat       GUIDO
/dev/sdc1     
   EE7C-337F                              vfat     
  KINGSTON

================================ Mount points: =================================

Device  
         Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/initrd.gz                                 1
            ?? = ??             boot/vmlinuz                                   1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 8a 14 00 fe  |................|
000001d0  ff ff 05 fe ff ff b3 cc  8a 14 4f a3 df 00 00 00  |..........O.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Please help me, I have a lot of information in my ubuntu partition, and i have not a backup [-o<

Thank you in advance,

Guido

---

