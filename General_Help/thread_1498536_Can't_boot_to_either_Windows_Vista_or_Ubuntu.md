---
title: "Can't boot to either Windows Vista or Ubuntu"
date: 2010-05-31
forum: General Help
---

### Post by Z47isthenew42 on 2010-05-31
Well, I messed up my computer and now I can't boot into Windows Vista or Ubuntu 9.10 Karmic Koala (I have yet to acquire a 10.04 Lucid Lynx disc, my connection's too slow to download and I'm apparently ineligible to request any more CDs through shipit).  I think I accidentally deleted Grub 2 as I get the grub rescue> prompt and my 9.10 LiveCD no longer works properly (it says "Authentication Error" and then goes to the log-in screen).

After some searching, I found some commands to try from [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode).

First I followed the directions about booting from the command line after using the ls command to determine where Ubuntu was (in my case (hd0,6) or sda6)

```
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
linux /vmlinuz root=/dev/sd06
```

After I enter the line beginning with "linux", I receive an "Unknown command 'linux'" error.

I then scrolled down to the section titled "Rescue Mode" and began following the code instructions there:

```
ls
set prefix=(hd0,6)/boot/grub/
set root=(hd0,6)
set
ls /boot/
insmod /boot/grub/linux.mod 
```

I get an error "file not found" after typing insmod /boot/grub/linux.mod.  I also notice that after I use ls /boot/, I don't see initrd images, but I do see an initrd.img  when typing ls (hd0,6)/.

When I boot into the 9.04 CD, open a terminal and run the follwing

```
sudo fdisk -l
```

I get the follwing output:

Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x70000000 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           8       64228+  de  Dell Utility 
/dev/sda2               9        1314    10485760    7  HPFS/NTFS 
/dev/sda3   *        1314       12003    85863424    7  HPFS/NTFS 
/dev/sda4           12004       14594    20805200    f  W95 Ext'd (LBA) 
/dev/sda5           14267       14594     2620416   dd  Unknown 
/dev/sda6           12004       14167    17382298+  83  Linux 
/dev/sda7           14168       14266      795186   82  Linux swap / Solaris

---

### Post by wilee-nilee on 2010-05-31
From the live cd that works run this script and post it in code tags. [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Z47isthenew42 on 2010-06-01
Okay, I did as asked and here's the output:  (the formatting might not be 100% because I needed to resave the file as a .doc file in order to copy and paste it on my other computer)

```
                Boot Info Script 0.55    dated February 15th, 2010                     
 
============================= Boot Info Summary: ============================== 
 
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in  
    partition #6 for /media/sda6/boot/grub. 
 => No boot loader is installed in the MBR of /dev/sdb 
 
sda1: _________________________________________________________________________ 
 
    File system:       vfat 
    Boot sector type:  Dell Utility: Fat16 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files/dirs:   /COMMAND.COM 
 
sda2: _________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files/dirs:    
 
sda3: _________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  Windows Vista 
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
 
sda4: _________________________________________________________________________ 
 
    File system:       Extended Partition 
    Boot sector type:  - 
    Boot sector info:   
 
sda5: _________________________________________________________________________ 
 
    File system:       vfat 
    Boot sector type:  Vista: Fat 32 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  Windows XP 
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM 
 
sda6: _________________________________________________________________________ 
 
    File system:       ext4 
    Boot sector type:  - 
    Boot sector info:   
    Operating System:  Ubuntu 9.10 
    Boot files/dirs:   /etc/fstab 
 
sda7: _________________________________________________________________________ 
 
    File system:       swap 
    Boot sector type:  - 
    Boot sector info:   
 
sdb1: _________________________________________________________________________ 
 
    File system:       vfat 
    Boot sector type:  Unknown 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files/dirs:    
 
=========================== Drive/Partition Info: ============================= 
 
Drive: sda ___________________ _____________________________________________________ 
 
Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x70000000 
 
Partition  Boot         Start           End          Size  Id System 
 
/dev/sda1                  63       128,519       128,457  de Dell Utility 
/dev/sda2             129,024    21,100,543    20,971,520   7 HPFS/NTFS 
/dev/sda3    *     21,100,544   192,827,391   171,726,848   7 HPFS/NTFS 
/dev/sda4         192,828,256   234,438,655    41,610,400   f W95 Ext d (LBA) 
/dev/sda5         229,197,824   234,438,655     5,240,832  dd Dell Media Direct 
/dev/sda6         192,828,258   227,592,854    34,764,597  83 Linux 
/dev/sda7         227,592,918   229,183,289     1,590,372  82 Linux swap / Solaris 
 
 
Drive: sdb ___________________ _____________________________________________________ 
 
Disk /dev/sdb: 2000 MB, 2000682496 bytes 
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x00000000 
 
Partition  Boot         Start           End          Size  Id System 
 
/dev/sdb1                 129     3,907,007     3,906,879   6 FAT16 
 
 
blkid -c /dev/null: ____________________________________________________________ 
 
Device           UUID                                   TYPE       LABEL                          
 
/dev/loop0                                              squashfs                                  
/dev/sda1        07D8-011A                              vfat       DellUtility                    
/dev/sda2        8EE0CEF8E0CEE595                       ntfs       RECOVERY                       
/dev/sda3        FE92885F92881E71                       ntfs       OS                             
/dev/sda5        40D6-4C35                              vfat       MEDIADIRECT                    
/dev/sda6        7944d157-2adf-4519-8e5a-678d3375d620   ext4                                      
/dev/sda7        c5d5e474-4b2b-42fa-8812-78635fc09aad   swap                                      
/dev/sdb1        D80F-1557                              vfat       Cruzer                         
 
============================ "mount | grep ^/dev  output: =========================== 
 
Device           Mount_Point              Type       Options 
 
rootfs           /                        rootfs     (rw) 
/dev/sr0         /cdrom                   iso9660    (ro,noatime) 
/dev/loop0       /rofs                    squashfs   (ro,noatime) 
/dev/sdb1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush) 
 
 
================================ sda5/boot.ini: ================================ 
 
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 
 
=============================== sda6/etc/fstab: =============================== 
 
# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sda6 during installation 
UUID=7944d157-2adf-4519-8e5a-678d3375d620 /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda7 during installation 
UUID=c5d5e474-4b2b-42fa-8812-78635fc09aad none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 
=================== sda6: Location of files loaded by Grub: =================== 
 
 
 100.8GB: boot/vmlinuz-2.6.31-14-generic 
 100.8GB: vmlinuz 
=========================== Unknown MBRs/Boot Sectors/etc ======================= 
 
Unknown BootLoader  on sdb1 
 
00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 40 01 00  |.<.MSDOS5.0..@..| 
00000010  02 00 02 00 00 f8 ef 00  3f 00 40 00 81 00 00 00  |........?.@.....| 
00000020  3f 9d 3b 00 80 00 29 57  15 0f d8 4e 4f 20 4e 41  |?.;...)W...NO NA| 
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.| 
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.| 
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......| 
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...| 
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.| 
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..| 
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.| 
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..| 
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..| 
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`| 
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... | 
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.| 
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......| 
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....| 
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.| 
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......| 
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..| 
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B| 
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............| 
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..| 
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..| 
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 53 79 73  |..'..Invalid Sys| 
00000190  74 65 6d 20 44 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem Disk...Disk | 
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl| 
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an| 
000001c0  64 20 74 68 65 6e 20 50  72 65 73 73 20 41 6e 79  |d then Press Any| 
000001d0  20 4b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | Key....IO      | 
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..| 
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.| 
00000200 
 

```

I'm positive that sdb is simply my flash drive.

---

### Post by Z47isthenew42 on 2010-06-03
I keep looking at the output of the Boot Info Script, but I have no idea what I'm supposed to be looking for, so I have no idea what to do.  :confused:

---

### Post by oldfred on 2010-06-04
I think you may have deleted more than just grub2 but some or most of the boot files in /boot.

I do not see
initrd.img
or any of the versions that should also be there.

kansasnoob has some good chroot commands as he has made then all one line to copy & paste rather than the 6 or 7 lines otherwise. But you do have to change to your partition sda6.
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Once chrooted into your system:

Commands once in chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

grub-install /dev/sda
grub-install --recheck /dev/sda

---

### Post by Z47isthenew42 on 2010-06-04
If I'm reading the commands correctly, it looks like I would need to get my laptop connected to the Internet.  Looks like I'll have to find a wired network somewhere.  But I also have a question.  How would I go about this since my 9.10 CD is not working properly, but my 9.04 CD sort of is and Grub2 wasn't introduced as the default until 9.10?

---

### Post by oldfred on 2010-06-04
It is my understanding once you have chrooted into your system you are updating the install and it is not using the system you booted except as the kernel to chroot boot. All updates are applied to the broken system so you can repair it. Those updates do not come from the CD.

---

### Post by Z47isthenew42 on 2010-06-04
oldfred, I didn't do the chroot commands, but I managed to get my 9.10 LiveCD working properly and re-installed.  I did check the disc for defects and it found one, but I'm not sure if that had anything with getting the CD to work.  I can now boot into both Ubuntu and Windows again, so I'll mark this thread as solved as soon as I remember how to.

---

