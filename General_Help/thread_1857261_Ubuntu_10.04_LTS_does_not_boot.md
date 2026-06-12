---
title: "Ubuntu 10.04 LTS does not boot"
date: 2011-10-10
forum: General Help
---

### Post by neela on 2011-10-10
Stops at the Grub rescue screen. i put in the rescue CD, and installed grub again. Then i got to the grub prompt. Now I try to set root to (hd0), or (hd0,1), or (hd0,5). I get unknown filesystem in each case.

Before I logged off, I was trying to reformat a flash drive, and/or rename it. I may have also tried to change the file system to ext2 -- but I may have accidentally done it to my hard drive. I am sorry for sounding sufficiently vague. I am not usually this incompetent.

Would appreciate any help in fixing my system -- starting with how does not one boot from the grub prompt if one doesn't know where the root file system, or where the kernel image is etc.      


Thanks a lot.
neela

---

### Post by mastablasta on 2011-10-10
First download this bootinfoscript: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
boot from liveCD and follow the instrucitons found on the site. this script will show up what exactly you did to your ocmputer, where your grub is etc.

---

### Post by Rubi1200 on 2011-10-10
+1 to the boot info script. 

It will really help us help you sort this out.

---

### Post by neela on 2011-10-10
Here is the output from the bootinfo script. Please see text attachment. I really appreciate the quick response.

Thank you.
Neela

---

### Post by Rubi1200 on 2011-10-11
For those concerned:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (dt3-root)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

dt3-root': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

dt3-swap_1': ___________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   312,498,175   311,996,418   5 Extended
/dev/sda5             501,760   312,498,175   311,996,416  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/dt3-root d4e5c0d6-ac98-43fd-b2f3-5dbe2d01fe85   ext4       
/dev/sda1        382bd1ae-b02b-4f46-bc1d-12db99f5cd1b   ext3       usb-pen
/dev/sda5        tBM6SO-adHO-AmBn-B5uT-64mx-e02O-Kl0Aaq LVM2_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
dt3-root
dt3-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/dt3-root /                        ext4       (rw,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  5f 1b 00 00 60 1b 00 00  6e 1b 00 00 8b 1b 00 00  |_...`...n.......|
00000010  d4 1b 00 00 08 1d 00 00  73 1d 00 00 a3 1d 00 00  |........s.......|
00000020  0a 1e 00 00 1b 1e 00 00  1c 1e 00 00 db 1e 00 00  |................|
00000030  8e 1f 00 00 37 20 00 00  b6 20 00 00 c6 20 00 00  |....7 ... ... ..|
00000040  e2 20 00 00 06 21 00 00  16 21 00 00 36 21 00 00  |. ...!...!..6!..|
00000050  37 21 00 00 6e 21 00 00  85 21 00 00 d7 21 00 00  |7!..n!...!...!..|
00000060  f2 21 00 00 0f 22 00 00  86 22 00 00 08 23 00 00  |.!..."..."...#..|
00000070  18 23 00 00 34 23 00 00  58 23 00 00 68 23 00 00  |.#..4#..X#..h#..|
00000080  88 23 00 00 89 23 00 00  c0 23 00 00 d7 23 00 00  |.#...#...#...#..|
00000090  29 24 00 00 61 24 00 00  71 24 00 00 64 25 00 00  |)$..a$..q$..d%..|
000000a0  69 25 00 00 e5 25 00 00  0f 26 00 00 8e 26 00 00  |i%...%...&...&..|
000000b0  9e 26 00 00 ba 26 00 00  de 26 00 00 ee 26 00 00  |.&...&...&...&..|
000000c0  0e 27 00 00 0f 27 00 00  46 27 00 00 5d 27 00 00  |.'...'..F'..]'..|
000000d0  af 27 00 00 ca 27 00 00  e7 27 00 00 5e 28 00 00  |.'...'...'..^(..|
000000e0  e0 28 00 00 f0 28 00 00  0c 29 00 00 30 29 00 00  |.(...(...)..0)..|
000000f0  40 29 00 00 60 29 00 00  61 29 00 00 98 29 00 00  |@)..`)..a)...)..|
00000100  af 29 00 00 01 2a 00 00  39 2a 00 00 49 2a 00 00  |.)...*..9*..I*..|
00000110  3c 2b 00 00 41 2b 00 00  bd 2b 00 00 12 2c 00 00  |<+..A+...+...,..|
00000120  1b 2c 00 00 1e 2c 00 00  23 2c 00 00 24 2c 00 00  |.,...,..#,..$,..|
00000130  2d 2c 00 00 2e 2c 00 00  5a 2d 00 00 85 2d 00 00  |-,...,..Z-...-..|
00000140  87 2d 00 00 97 2d 00 00  b3 2d 00 00 b4 2d 00 00  |.-...-...-...-..|
00000150  cb 2d 00 00 f1 2d 00 00  27 2e 00 00 39 2e 00 00  |.-...-..'...9...|
00000160  84 2e 00 00 85 2e 00 00  a0 2e 00 00 bf 2e 00 00  |................|
00000170  17 2f 00 00 33 2f 00 00  37 2f 00 00 53 2f 00 00  |./..3/..7/..S/..|
00000180  7f 2f 00 00 81 2f 00 00  88 2f 00 00 8b 2f 00 00  |./.../.../.../..|
00000190  90 2f 00 00 91 2f 00 00  92 2f 00 00 95 2f 00 00  |./.../.../.../..|
000001a0  9a 2f 00 00 9b 2f 00 00  af 2f 00 00 bd 2f 00 00  |./.../.../.../..|
000001b0  08 30 00 00 2a 30 00 00  3a 30 00 00 46 30 00 3b  |.0..*0..:0..F0.;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 b0 98 12 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on dt3-root'


Unknown BootLoader on dt3-swap_1'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/dt3-root': No such file or directory
hexdump: /dev/mapper/dt3-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/dt3-swap_1': No such file or directory
hexdump: /dev/mapper/dt3-swap_1': No such file or directory


```

---

### Post by raja.genupula on 2011-10-11
[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#A.27.27grub.3E.27.27_Prompt_Booting](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#A.27.27grub.3E.27.27_Prompt_Booting)


look at that

---

### Post by neela on 2011-10-11
Thanks.

So if I see this on the report:
dt3-root': 
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''



How do I fix the fact that the boot sector is unknown?

Neela

---

### Post by oldfred on 2011-10-12
Did you intentionally convert to LVM. It is a bit more advanced in that it offers logical partitions as an overlay over physical partitions.

Install this in liveCD and rerun boot script. Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

---

### Post by neela on 2011-10-13
Thank you. I will try that.

---

