---
title: "GRUB won't go away"
date: 2010-11-09
forum: General Help
---

### Post by aerospace_guy_ on 2010-11-09
Hi all,

I've searched all over for an answer to this odd behavior of GRUB,

I've recently upgraded my computer, and installed windows, I haven't gotten around to putting Ubuntu on it yet, but every once and a while GRUB will re-assert itself and I won't be able to boot windows until I fix the MBR using the windows installation CD. what makes this weird is the fact that the disk that GRUB was initially installed on is now part of a RAID array in my computer which Windows has written its own MBR code to.

does anyone know why GRUB keeps coming back at random like this even though the disk partition it was on is no longer in existence?

would installing 10.10 and GRUB2 along with it solve this problem?

thanks for any help

EDIT: I forgot to mention when grub does try to boot the system, it starts to load, and then stops with error 16 which I believe means that it can't actually find a bootable system partition, this makes sense since Ubuntu is no longer on my system.

---

### Post by wilee-nilee on 2010-11-09
Post the bootscript in my signature in codetags. code tags are just highlighting the pasted text and hitting the # in the reply panel. My sig has manual instructions for code tags as well.

Generally the script may not work perfectly if you have a raid setup but it is a good start anyways.

---

### Post by wilee-nilee on 2010-11-09
If your waiting for some magic fix for this, I suggest you stock up on the essentials you need. There may be one but the chances of somebody seeing your thread and helping are diminished with no information more then you have given.

---

### Post by aerospace_guy_ on 2010-11-09
Thanks for your quick reply, I've been at school all day and unable to respond.

here are the results of the boot script.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x613bf9d1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   251,656,191   251,449,344   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
256 heads, 63 sectors/track, 9691 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb2         264,192   312,473,599   312,209,408 Linux or Data

/dev/sdb2 ends after the last sector of /dev/sdb
Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdd1        00FA-8080                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd1        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  00 01 02 03 04 05 06 07  08 09 0a 0b 0c 0d 0e 0f  |................|
00000010  10 11 12 13 14 15 16 17  18 19 1a 1b 1c 1d 1e 1f  |................|
00000020  20 21 22 23 24 25 26 27  28 29 2a 2b 2c 2d 2e 2f  | !"#$%&'()*+,-./|
00000030  30 31 32 33 34 35 36 37  38 39 3a 3b 3c 3d 3e 3f  |0123456789:;<=>?|
00000040  40 41 42 43 44 45 46 47  48 49 4a 4b 4c 4d 4e 4f  |@ABCDEFGHIJKLMNO|
00000050  50 51 52 53 54 55 56 57  58 59 5a 5b 5c 5d 5e 5f  |PQRSTUVWXYZ[\]^_|
00000060  60 61 62 63 64 65 66 67  68 69 6a 6b 6c 6d 6e 6f  |`abcdefghijklmno|
00000070  70 71 72 73 74 75 76 77  78 79 7a 7b 7c 7d 7e 7f  |pqrstuvwxyz{|}~.|
00000080  80 81 82 83 84 85 86 87  88 89 8a 8b 8c 8d 8e 8f  |................|
00000090  90 91 92 93 94 95 96 97  98 99 9a 9b 9c 9d 9e 9f  |................|
000000a0  a0 a1 a2 a3 a4 a5 a6 a7  a8 a9 aa ab ac ad ae af  |................|
000000b0  b0 b1 b2 b3 b4 b5 b6 b7  b8 b9 ba bb bc bd be bf  |................|
000000c0  c0 c1 c2 c3 c4 c5 c6 c7  c8 c9 ca cb cc cd ce cf  |................|
000000d0  d0 d1 d2 d3 d4 d5 d6 d7  d8 d9 da db dc dd de df  |................|
000000e0  e0 e1 e2 e3 e4 e5 e6 e7  e8 e9 ea eb ec ed ee ef  |................|
000000f0  f0 f1 f2 f3 f4 f5 f6 f7  f8 f9 fa fb fc fd fe ff  |................|
00000100  00 01 02 03 04 05 06 07  08 09 0a 0b 0c 0d 0e 0f  |................|
00000110  10 11 12 13 14 15 16 17  18 19 1a 1b 1c 1d 1e 1f  |................|
00000120  20 21 22 23 24 25 26 27  28 29 2a 2b 2c 2d 2e 2f  | !"#$%&'()*+,-./|
00000130  30 31 32 33 34 35 36 37  38 39 3a 3b 3c 3d 3e 3f  |0123456789:;<=>?|
00000140  40 41 42 43 44 45 46 47  48 49 4a 4b 4c 4d 4e 4f  |@ABCDEFGHIJKLMNO|
00000150  50 51 52 53 54 55 56 57  58 59 5a 5b 5c 5d 5e 5f  |PQRSTUVWXYZ[\]^_|
00000160  60 61 62 63 64 65 66 67  68 69 6a 6b 6c 6d 6e 6f  |`abcdefghijklmno|
00000170  70 71 72 73 74 75 76 77  78 79 7a 7b 7c 7d 7e 7f  |pqrstuvwxyz{|}~.|
00000180  80 81 82 83 84 85 86 87  88 89 8a 8b 8c 8d 8e 8f  |................|
00000190  90 91 92 93 94 95 96 97  98 99 9a 9b 9c 9d 9e 9f  |................|
000001a0  a0 a1 a2 a3 a4 a5 a6 a7  a8 a9 aa ab ac ad ae af  |................|
000001b0  b0 b1 b2 b3 b4 b5 b6 b7  b8 b9 ba bb bc bd be bf  |................|
000001c0  c0 c1 c2 c3 c4 c5 c6 c7  c8 c9 ca cb cc cd ce cf  |................|
000001d0  d0 d1 d2 d3 d4 d5 d6 d7  d8 d9 da db dc dd de df  |................|
000001e0  e0 e1 e2 e3 e4 e5 e6 e7  e8 e9 ea eb ec ed ee ef  |................|
000001f0  f0 f1 f2 f3 f4 f5 f6 f7  f8 f9 fa fb fc fd fe ff  |................|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory


```

---

### Post by oldfred on 2010-11-09
The only way you get grub legacy to boot is if you have the 4GB USB flash drive set to boot first from BIOS and only some times have it plugged in. When in, it tries to boot old grub.

You also seem to have some issues or are using special partitions on sda and you have gpt on sdb. Part of the script cannot parse sda but the fdisk does show the partitions. Many of the older tools for Linux do not totally parse the gpt partitions, but Linux works fine with gpt. sdc does not even look like it is formated?

---

### Post by aerospace_guy_ on 2010-11-09
thanks for your input, I'd forgotten that a while ago I'd installed a version of linux on my memory key, that explains why this booting phenomenon is so hit-and-miss.

it looks like re-formatting the USB-key and getting rid of the boot data it contains should solve the problem.

you are correct sdc is not formatted, as I mentioned earlier I haven't gotten around to installing UBUNTU yet, but I left a section of my RAID array free for it when I set it up.

---

### Post by srs5694 on 2010-11-09
One more observation: /dev/sdb is reported as having 156,301,488 sectors (74.5 GiB), but the partitions it contains extend out to 312,473,599 sectors (149.0 GiB), and the protective EFI GPT partition in the MBR goes out to 4,294,967,295 (which is invalid but makes a sort of sense as an error, since this is the maximum size for an MBR partition). This is all, at best, very very weird. I suggest you treat that disk very carefully, since it could be badly damaged. As the author of [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) I'd be interested in seeing what gdisk has to say about it, particularly if you run the "p" (display partitions) and "v" (verify) functions on it. (Doing this will do no harm; gdisk won't write to the disk unless you use the "w" option or certain other obscure options.) If you could post the output of gdisk with those commands, ideally between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility, I might be able to offer more advice about that disk's oddness.

---

### Post by aerospace_guy_ on 2010-11-10
Here's the results from gdisk

the disk has changed slightly as I've made a third partition for PS-scratch disks on the first logical disk in the array.

using p mode for the raid disks:

```

Disk 1:: 251658240 sectors, 120.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): EFBCE2F0-EC33-6855-AEA6-00D059ABDC76
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 251658206
Partitions will be aligned on 2048-sector boundaries
Total free space is 6077 sectors (3.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  Linux/Windows data
   2          206848       218888191   104.3 GiB   0700  Linux/Windows data
   3       218888192       251654143   15.6 GiB    0700  Linux/Windows data

Disk 2:: 217217024 sectors, 103.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5B619672-483B-41F0-AE26-BDC40550F76E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 217216990
Partitions will be aligned on 2-sector boundaries
Total free space is 216954813 sectors (103.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part


```

and using v mode:

```

for disk 1:
No problems found. 6077 free sectors (3.0 MiB) available in 2
segments, the largest of which is 4063 (2.0 MiB) in size.

for disk 2:
No problems found. 216954813 free sectors (103.5 GiB) available in 1
segments, the largest of which is 216954813 (103.5 GiB) in size.

```

Disk 0 comes up as my data drive which is not in question here as it was not included in the script code in my earlier post

hopefully this might clear things up

---

### Post by srs5694 on 2010-11-10
Actually, the gdisk output just muddies the waters. The disk sizes reported in the gdisk output doesn't match the sizes reported in the Boot Info Script output, and you've trimmed some of the initial gdisk output (the partition table scan results) and re-labelled the disks ("disk 1" and "disk 2", which gdisk doesn't use), so it's not clear to me what should correspond to what. I suspect there's some sort of RAID difference going on here -- one set of results or the other may be reporting the "raw" disk data and the other may be looking at the disks as seen via RAID drivers or controllers. Perhaps you should elaborate on your RAID setup -- are you using a hardware RAID configuration or a motherboard-based software RAID (often called "fake RAID," although I personally dislike that term). (I can't see how it could be a Linux software RAID setup, since that would require RAID partitions that aren't apparent in any of the outputs you've posted.)

---

### Post by aerospace_guy_ on 2010-11-10
sorry about the confusion with the disk names, I ran gdisk in windows so I believe it is reporting back the disk configuration based on what is seen via the RAID controller. I was also confused, since my data disk which is physically on port 8 came up as disk 0 in gdisk while my RAID disks came up as disks 1 and 2.

as for the RAID setup, it's 3, 80GB disks in RAID0 using a motherboard RAID controller, however based on my research, it seems to be somewhat of a hybrid between a regular software controller and a hardware controller, perhaps someone might know a bit more, it's the RAID controller built into the intel ICH10R chipset. (The board does have a built in fully hardware controlled RAID chip, but it's only got two ports so I'm still getting better speed from the intel controller with 3 disks.)

The three disks are set up by the controller to appear to the operating systems as two logical disks, 120GB and 103.6GB. 

The 120GB drive has been further partitioned by windows7 to include the 100MB system files partition, and I have taken 16GB off the end for swap space.

The 103.6GB drive has not had anything done to it save being initialized by windows which was a mistake on my part, and will be reversed when I install UBUNTU.

I will start up the computer using a Live-CD and re-run gdisk and see how the results differ.

in case you're wondering my motherboard is the GIGABYTE GA-X58A-UD5.

---

### Post by aerospace_guy_ on 2010-11-10
here's the results from the live-CD run:

using p mode:
```

Disk /dev/sda: 156301488 sectors, 74.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): C5BA9DA5-976F-42D8-9E28-9B2B72479B78
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 156301454
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  Linux/Windows data
   2          206848       218888191   104.3 GiB   0700  Linux/Windows data
   3       218888192       251654143   15.6 GiB    0700  Linux/Windows data


Disk /dev/sdb: 156301488 sectors, 74.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8ABD6DDC-A711-40DB-8FC1-534DD9A5444A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312475614
Partitions will be aligned on 2-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192       312473599   148.9 GiB   0700  Basic data partition

Disk /dev/sdc: 156301488 sectors, 74.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6FE03A85-3BCD-48EE-8671-493D533DE2E1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 156301454
Partitions will be aligned on 2048-sector boundaries
Total free space is 156301421 sectors (74.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name


```

and using v mode:
for sda
```


Problem: partition 2 is too big for the disk.

Problem: partition 3 is too big for the disk.

Warning! Secondary partition table overlaps the last partition by
95352689 blocks!
You will need to delete this partition or resize it in another utility.

Identified 3 problems!

```
for sdb
```

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 156301488 sectors, needs to be 312475647 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: partition 2 is too big for the disk.

Identified 4 problems!

```
for sdc
```

Command (? for help): v
No problems found. 156301421 free sectors (74.5 GiB) available in 1
segments, the largest of which is 156301421 (74.5 GiB) in size.

```

obviously there is something different going on here than in windows, I have to get to school now, but I'll check back later to see your thoughts on the matter.

---

### Post by srs5694 on 2010-11-10
Yes, Linux and Windows are clearly seeing the disks in different ways. My suspicion is that your motherboard RAID is really software RAID and either Linux lacks drivers for this particular variety of motherboard software RAID or the Linux drivers are buggy or misconfigured. Alternatively, perhaps you've got RAID devices for the disk in the /dev/mapper directory or as /dev/md* devices, and the /dev/sd* devices are still accessible, but are essentially meaningless. Please check the /dev/mapper and /dev/md* locations and report back what you've got.

Also, you've continued to omit the gdisk partition table scan, which should look like this:

```

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

```

This information is critical, since it reveals whether gdisk is reading GPT data native to the disk or if it's converting MBR data into GPT form and reporting the results.

More broadly speaking, my impression is that motherboard software RAID solutions are so troublesome that they should be avoided in most cases. Since you're using RAID 0, you're not relying on RAID for extra reliability, just to make your three disks look like two disks, and perhaps for speed if you're using striping. I recommend you wipe the disks, disable RAID, and re-install Windows and Linux without using RAID, despite the fact that you won't be able to have such big partitions. I believe you should be able to employ the Windows "dynamic disks" feature to create bigger aggregate Windows partitions, if necessary; and Linux Logical Volume Manager (LVM) can do the same for Linux. LVM, at least, can employ striping for extra speed, if you want that. Be careful when implementing these features, though; you don't want either one to grab all the available space.

---

### Post by aerospace_guy_ on 2010-11-11
here are the partition table scan in the following order: 
Windows disk 1 
windows disk 2 
Ubuntu sda 
Ubuntu sdb 
Ubuntu sdc 
 
```

 
Partition table scan: 
  MBR: MBR only 
  BSD: not present 
  APM: not present 
  GPT: not present 
 
------------------------------------------------------------ 
Partition table scan: 
  MBR: protective 
  BSD: not present 
  APM: not present 
  GPT: present 
------------------------------------------------------------
Type device filename, or press <Enter> to exit: /dev/sda
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

------------------------------------------------------------
Type device filename, or press <Enter> to exit: /dev/sdb
Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged


--------------------------------------------------------------
Type device filename, or press <Enter> to exit: /dev/sdc
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.


```

I've tried looking for the /dev/mapper, /dev/md* and /dev/sd* directories, but I can't find them. could this have anything to do with the fact that this is an 8.04 live-CD (sorry I'm a relative linux noob and use it mainly as a rendering platform)

as for getting rid of the RAID system, unless I absolutely can't get linux to install on it I won't be getting rid of it as it effectively doubles the speed of the fastest disk I have available, and I don't have money to get a Solid State Drive right now. the point was never to increase space, my previous main drive was a 250GB drive anyway, it's just quite slow.

---

### Post by dcstar on 2010-11-11
> **aerospace_guy_ said:**
> Hi all,

I've searched all over for an answer to this odd behaviour of GRUB,

I've recently upgraded my computer, and installed windows, I haven't gotten around to putting Ubuntu on it yet, but every once and a while GRUB will re-assert itself and I won't be able to boot windows until I fix the MBR using the windows installation CD.
........

Grub is not "reasserting itself", your PC is selecting the drive that still has Grub on it to boot off.

Go into the BIOS and remove that drive from the boot sequence, or put in a boot delay so the other drives that are supposed to be booted have time to spin up correctly, or overwrite the MBR of the drive with the Grub bootloader still on it.

---

### Post by aerospace_guy_ on 2010-11-11
ok so I downloaded 10.10 and am now running from that live CD and it seems to recognise the disks properly in the file browser, they all come up as they are configured based on the RAID controller.

there are also some files in the /dev/mapper folder (for starters, the /dev/mapper folder actually exists):
control
isw_cjdichchbg_MAIN
isw_cjdichchbg_MAIN1
isw_cjdichchbg_MAIN2
isw_cjdichchbg_MAIN3
isw_cjdichchbg_UBUNTU

---

### Post by srs5694 on 2010-11-11
8.04 is two and a half years old, so if you've got a newer motherboard than that, it's not surprising that it wasn't correctly detecting your motherboard's software RAID setup.

It sounds from your latest message as if 10.10 is working correctly, but I'm not very familiar with installing Ubuntu on motherboard software RAID configurations, so I can't offer you much more advice on that score.

If you have more problems, I recommend you start a new thread with a title that better reflects whatever problem you have with the 10.10 installation; this thread has long since stopped being about GRUB, and a title that reflects the current problem might attract people with the relevant expertise to solve the problem.

---

### Post by aerospace_guy_ on 2010-11-11
Thank you very much for your help. Installing 10.10 seems to have been a success but if I have any more problems, I'll start a new thread.

---

