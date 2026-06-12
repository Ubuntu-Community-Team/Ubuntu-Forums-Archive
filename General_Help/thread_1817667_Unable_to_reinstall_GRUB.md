---
title: "Unable to reinstall GRUB"
date: 2011-08-03
forum: General Help
---

### Post by Zanon on 2011-08-03
My dual booting Unbuntu/windows computer is failing to boot. I have tried to reinstall GRUB but have so far been unsuccessful.

I used the Ubuntu Secured 64bits live CD  to run “Boot Repair” and this reported:

[INDENT]“There is no boot backup on this computer. This will reinstall GRUB bootloader. Do you want to continue?”.[/INDENT]

On continuing, "Boot Repair" reported under "Last Confirmation/Advanced Options":

[INDENT] “(Requires internet) Manually purge and reinstall the GRUB of: Ubuntu 11-04 (sdb1)”.[/INDENT] 

When I click “Apply”, Boot Repair asks me to enter the following in a terminal:

[INDENT]sudo chroot /mnt/clean/sdb1 apt-get install -y grub-pc[/INDENT]

However, the terminal then responds:

[INDENT]chroot: failed to run command ‘apt-get’ : No such file or directory.[/INDENT]

Which was quite disappointing!:confused:

I have also tried Super Grub2 Disk and Rescatux and these also failed.

I entered "sudo fdisk -l" and this seemed to identify all the disks and partitions corrected (I will supply the terminal output in a following post). The only issue is that I expected sdb1 to be indicated as Boot, but it wasn't.

I would be very grateful for any help or advice.

Kind regards,

Adrian

---

### Post by TeoBigusGeekus on 2011-08-03
Try with [this]("https://help.ubuntu.com/community/Grub2#ChRoot").

---

### Post by Zanon on 2011-08-03
Hi TeoBigusGeekus,

Many thanks for your quick reply.:)

This is the report I got when I entered sudo fdisk -l:[INDENT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79372110

   Device       Boot         Start             End            Blocks            Id        System
/dev/sda1       *                    1       19458      156288000     7      HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c4021f0

   Device       Boot         Start             End            Blocks            Id        System
/dev/sdb1                                 1         57325     460456960      83        Linux
/dev/sdb2                     57325         60801       27925025+         5         Extended
/dev/sdb5                    58337          60801        19800081       82         Linux swap / Solaris
/dev/sdb6                    57325         58336           8124416        82        Linux swap / Solaris

Partition table entries are not in disk order

[/INDENT](I'm really sorry about the formatting above but I don't seem to be able to get it any better; the only thing [I think] it really shows is that I would have expected sdb1 to be shown with * to indicate Boot.) 

I followed the guidance that you kindly supplied and entered:[INDENT]sudo mount /dev/sdb1 /mnt
[/INDENT]And the report I got back was:[INDENT]mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]I also entered dmesg | tail and this showed:[INDENT][ 5514.780924] sd 3:0:0:0: [sdb]  Sense Key : Aborted Command [current] [descriptor]
[ 5514.780932] Descriptor sense data with sense descriptors (in hex):
[ 5514.780936]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 5514.780953]         34 c0 08 08 
[ 5514.780960] sd 3:0:0:0: [sdb]  Add. Sense: No additional sense information
[ 5514.780967] sd 3:0:0:0: [sdb] CDB: Write(10): 2a 00 33 81 21 60 00 00 08 00
[ 5514.780982] end_request: I/O error, dev sdb, sector 864100704
[ 5514.781013] ata4: EH complete
[ 5514.781030] JBD: recovery failed
[ 5514.781047] EXT4-fs (sdb1): error loading journal

[/INDENT]So I appear to be stuck on the very first step of the guidance you provided.:confused:

Any advice/guidance very welcome.

Kind regards,

Adrian

---

### Post by TeoBigusGeekus on 2011-08-03
Check the disk for errors
```
sudo fsck /dev/sdb1
```
and try again.

---

### Post by Zanon on 2011-08-03
Hi TeoBigusGeekus,

Many thanks again for your response! :)

I entered sudo fsck /dev/sdb1 and the response I got was:
[INDENT]fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/dev/sdb1: recovering journal
fsck.ext4: unable to set superblock flags on /dev/sdb1
[/INDENT]Which I assume means that the disk wasn't able to be checked for errors for some reason? :confused: 

Kind regards,

Adrian

---

### Post by TeoBigusGeekus on 2011-08-03
I think you have a disk failure there; either a hardware one or your data is totally messed up.
Unless anyone else has a better idea, I'd go with a reinstallation.

---

### Post by Zanon on 2011-08-03
Hi TeoBigusGeekus,

Many thanks for your time and advice! :)

You could well be right that there is a problem with the the disk although Disk Utility says the disk is healthy. However, I have been doing quite a lot of things to try to get my computer to boot (at one stage I was mistaenly tryinmg to install GRUB instead of GRUB2); so I have probably made the problem worse!:cry:

I saw another thread which made reference to a Boot Info Script so I'll try running that and post the results here later.

Thanks and best wishes! :)

Adrian

---

### Post by Zanon on 2011-08-03
I ran the Boot Info Script and this is the result:

  ```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid e1bce359-b3b5-47b9-859b-74531cd9c746 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   920,915,967   920,913,920  83 Linux
/dev/sdb2         920,918,014   976,768,064    55,850,051   5 Extended
/dev/sdb5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris
/dev/sdb6         920,918,016   937,166,847    16,248,832  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4244E25B44E250E9                       ntfs       
/dev/sdb1        e1bce359-b3b5-47b9-859b-74531cd9c746   ext4       
/dev/sdb5        fe6ca925-3d23-4a9b-87f2-90b10994fd39   swap       
/dev/sdb6        41bef6a5-9317-4a11-83d4-fe258270e2f2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  68 99 7b a9 30 31 77 62  80 01 00 00 ff fb 94 64  |h.{.01wb.......d|
00000010  04 0c 83 17 4c 54 9b 38  12 f0 39 66 ea e3 2d 03  |....LT.8..9f..-.|
00000020  5c 4c 4d 33 52 6d bc ab  c8 db 1d 6b 9c 92 8d 71  |\LM3Rm.....k...q|
00000030  e1 3f 44 23 99 b7 34 59  a7 4a 17 1d 9d 95 cd c5  |.?D#..4Y.J......|
00000040  e0 bb 75 a9 24 9e ee d8  86 66 e1 e5 b7 c0 63 05  |..u.$....f....c.|
00000050  b4 c8 1e 6a 59 67 24 98  e5 6d e1 70 71 ab 95 ac  |...jYg$..m.pq...|
00000060  6a 63 72 7b b9 d9 04 53  3b 18 a5 57 95 8c 62 a6  |jcr{...S;..W..b.|
00000070  cc eb bb ab ff fd 11 11  b3 3a 48 71 6c b7 25 10  |.........:Hql.%.|
00000080  fd 7f ed e1 c5 7f d2 ae  0f 27 1a 00 53 6e 05 92  |.........'..Sn..|
00000090  1a 3d ac 24 ea ab ff fa  99 e6 67 a3 c3 a5 00 32  |.=.$......g....2|
000000a0  ea bd 77 36 cd c0 fa 7f  c3 ca 35 2c ff a5 25 26  |..w6......5,..%&|
000000b0  56 32 c9 aa b7 7f e9 37  76 7e 1b 17 cc bc 10 eb  |V2.....7v~......|
000000c0  06 1f 8a 7f 00 05 c9 b8  70 cc 20 b4 58 5c d7 40  |........p. .X\.@|
000000d0  0a a2 87 1c 06 9f 34 ae  9c 3d 28 ec 66 f5 bd 39  |......4..=(.f..9|
000000e0  a2 5f 2b 9c a4 38 ab 05  db 71 1a 56 a3 d4 2c 31  |._+..8...q.V..,1|
000000f0  a9 dc 75 1a 05 d4 d5 dd  23 5f 31 7b cf ed 54 9d  |..u.....#_1{..T.|
00000100  e8 7e 56 91 1f ee a6 26  ef 57 69 56 8f 3b 51 3d  |.~V....&.WiV.;Q=|
00000110  2c a6 f7 39 0f 31 9a 8e  b5 6d cb e7 62 b9 aa d6  |,..9.1...m..b...|
00000120  ea e1 4e f8 b2 f5 0c 00  33 fd c0 8e b8 92 80 dd  |..N.....3.......|
00000130  42 bf e5 56 5b d1 19 0e  ac 38 60 32 21 d2 95 d4  |B..V[....8`2!...|
00000140  9f db d7 bf a6 fd cd 4c  ce b5 9f 3d e5 4b 7d e1  |.......L...=.K}.|
00000150  b5 22 cb ec cd 12 fc fc  dd a7 47 3c 16 0a 00 06  |."........G<....|
00000160  f7 e1 69 18 47 83 c5 82  70 0c 4a 3c 68 d9 9c 7d  |..i.G...p.J<h..}|
00000170  52 dd 90 bc 2e 4e 2e db  3a 62 c5 f0 57 4e 88 ca  |R....N..:b..WN..|
00000180  67 8d a8 03 4d 58 b9 70  85 bd 4b b8 30 30 64 63  |g...MX.p..K.00dc|
00000190  25 03 00 00 00 00 01 b6  94 3e fc 11 2a 7f fa d4  |%........>..*...|
000001a0  3e a2 8c aa ab 7a 5a a9  63 a9 13 53 2d 55 a3 d3  |>....zZ.c..S-U..|
000001b0  af af a7 52 c1 6c 48 38  99 f5 b3 d2 5f 5d 00 fe  |...R.lH8...._]..|
000001c0  ff ff 82 fe ff ff 21 f4  f7 00 22 40 5c 02 00 fe  |......!..."@\...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 f0 f7 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```Any advice on being able to boot my system welcome!

Kind regards,

Adrian

---

### Post by oldfred on 2011-08-03
If you want to try file checks one more time:

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sdb1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sdb1
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Zanon on 2011-08-07
Hi oldfred,

Many thanks for your help. I was able to boot my system after following your guidance.

I didn't seem to be getting the desired responses from the commands but I persevered as best I could. 

My system rebooted on the second restart. Once I got it started I reinstalled/updated Grub (I don't know if this was necessary) and everything has been working fine for for the last two days.

I'm not exactly sure what the problem was (all I can say is that it appeared that, for some reason, the disk/sdb1 wouldn't mount) but your guidance seemed to do the trick (but I'm not exactly sure how; I guess, somehow, it got the disk/sdb1 to mount)!

Many thanks for your time and advice!:P

Kind regards,

Adrian

---

