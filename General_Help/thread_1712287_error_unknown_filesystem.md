---
title: "error: unknown filesystem"
date: 2011-03-22
forum: General Help
---

### Post by beliyyal on 2011-03-22
Ok guys, having a bit of a problem here. I woke up this morning, and my computer was froze. It does this from time to time, the monitor won't respond and wake up, flashing lights in the keyboard etc. Well anyways, I turned it off, then turned it back on, and it says:
```
error: unknown filesystem
grub rescue >
```

I tried to reinstall the grub2 files using a live cd, and ran into somewhat of a big problem. I tried to mount /dev/sda1 /mnt/ but it kept saying ```
mount: you must specify the filesystem type

```

I opened the disk utility to try and mount it that way, and the largest chunk of my hard drive, that which used to be "ubuntu ext4" is now "unknown". 

[img]http://img16.imageshack.us/img16/4449/screenshot400gbharddisk.png[/img]

I really need some help here guys, any would be appreciated.

---

### Post by Rubi1200 on 2011-03-22
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by beliyyal on 2011-03-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Fat32
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   777,308,159   777,306,112  83 Linux
/dev/sda2         777,310,206   781,422,591     4,112,386   5 Extended
/dev/sda5         777,310,208   781,422,591     4,112,384  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        799c31c7-cb65-49df-8f1b-98dde607735e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  77 69 64 74 68 00 cb 08  77 20 52 6f 11 00 00 00  |width...w Ro....|
00000010  31 36 00 00 08 04 59 00  50 56 cf 08 11 00 00 00  |16....Y.PV......|
00000020  68 65 69 67 68 74 00 00  10 00 00 00 19 00 00 00  |height..........|
00000030  73 6f 64 69 70 6f 64 69  3a 64 6f 63 6e 61 6d 65  |sodipodi:docname|
00000040  00 55 b7 08 29 00 00 00  68 74 74 70 3a 2f 2f 63  |.U..)...http://c|
00000050  72 65 61 74 69 76 65 63  6f 6d 6d 6f 6e 73 2e 6f  |reativecommons.o|
00000060  72 67 2f 6e 73 23 00 08  77 20 52 6f 21 00 00 00  |rg/ns#..w Ro!...|
00000070  68 74 74 70 3a 2f 2f 77  77 77 2e 77 33 2e 6f 72  |http://www.w3.or|
00000080  67 2f 32 30 30 30 2f 73  76 67 00 00 21 00 00 00  |g/2000/svg..!...|
00000090  68 74 74 70 3a 2f 2f 77  77 77 2e 77 33 2e 6f 72  |http://www.w3.or|
000000a0  67 2f 32 30 30 30 2f 73  76 67 00 44 11 00 00 00  |g/2000/svg.D....|
000000b0  78 6d 6c 6e 73 3a 73 76  67 00 69 74 21 00 00 00  |xmlns:svg.it!...|
000000c0  68 74 74 70 3a 2f 2f 77  77 77 2e 77 33 2e 6f 72  |http://www.w3.or|
000000d0  67 2f 32 30 30 30 2f 73  76 67 00 00 69 00 00 00  |g/2000/svg..i...|
000000e0  e0 5e c4 08 48 81 c3 08  06 e2 3a ce 38 e3 cf 08  |.^..H.....:.8...|
000000f0  48 49 cf 08 94 77 4c 2b  58 55 bd 08 80 0a b8 08  |HI...wL+XU......|
00000100  c6 2d be 06 08 94 ce 08  38 55 bd 08 1c 34 ce 06  |.-......8U...4..|
00000110  58 13 af 08 70 49 cf 08  27 91 38 b7 d0 e3 d6 08  |X...pI..'.8.....|
00000120  b8 5e d0 08 d8 1c f5 14  00 00 00 00 00 00 00 00  |.^..............|
00000130  00 00 00 00 78 13 af 08  68 13 af 08 1b 0d 00 00  |....x...h.......|
00000140  00 00 00 00 29 00 00 00  68 74 74 70 3a 2f 2f 77  |....)...http://w|
00000150  77 77 2e 77 33 2e 6f 72  67 2f 32 30 30 30 2f 73  |ww.w3.org/2000/s|
00000160  76 67 00 08 f8 03 59 00  28 00 00 00 11 00 00 00  |vg....Y.(.......|
00000170  69 6d 61 67 65 2f 6a 70  65 67 00 00 21 00 00 00  |image/jpeg..!...|
00000180  68 74 74 70 3a 2f 2f 77  77 77 2e 77 33 2e 6f 72  |http://www.w3.or|
00000190  67 2f 32 30 30 30 2f 73  76 67 00 00 11 00 00 00  |g/2000/svg......|
000001a0  68 65 69 67 68 74 00 08  10 00 00 00 21 00 00 00  |height......!...|
000001b0  68 74 74 70 3a 2f 2f 77  77 77 2e 77 33 2e 6f 72  |http://www.w3.or|
000001c0  67 2f 32 30 30 30 2f 73  76 67 00 00 31 00 00 00  |g/2000/svg..1...|
000001d0  68 74 74 70 3a 2f 2f 77  77 77 2e 77 33 2e 6f 72  |http://www.w3.or|
000001e0  67 2f 31 39 39 39 2f 78  6c 69 6e 6b 00 00 00 00  |g/1999/xlink....|
000001f0  60 b2 b5 08 02 00 00 00  30 00 00 00 01 01 00 00  |`.......0.......|
00000200
```

---

### Post by kelvin spratt on 2011-03-22
Try doing a disc check with partedmagic live CD/flashdrive to see if it recovers the partition.

---

### Post by beliyyal on 2011-03-22
bump

---

### Post by beliyyal on 2011-03-23
...bump

---

### Post by Rubi1200 on 2011-03-23
Hi,

you can run a file-system check from the LiveCD to see if it repairs the installation:


```
sudo e2fsck -f -y -v /dev/sda1

```
Reboot, taking out the CD, and keep your fingers crossed.

---

### Post by beliyyal on 2011-03-28
> **Rubi1200 said:**
> Hi,

you can run a file-system check from the LiveCD to see if it repairs the installation:


```
sudo e2fsck -f -y -v /dev/sda1

```
Reboot, taking out the CD, and keep your fingers crossed.

Ok, finally got it working again. I did this twice, and also when it booted it, on the splash screen it said there were some problems with the disk, and gave me the option to press F to fix, press I to ignore, or press M to manually repair (or something). I pressed F, waited a few minutes, and it took me to my login screen. Thanks for the help man, you are a lifesaver.

---

### Post by Rubi1200 on 2011-03-28
No problem, you are more than welcome :)

---

