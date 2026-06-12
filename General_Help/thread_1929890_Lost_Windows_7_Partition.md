---
title: "Lost Windows 7 Partition"
date: 2012-02-22
forum: General Help
---

### Post by ericholte on 2012-02-22
Hope I'm in the right thread. I have a OEM Windows 7 laptop that I added an Ubuntu partition to. Later, I upgraded Ubuntu and selected NOT to have a separate swap partition, scared I might overwrite my Windows partition(I'm not very knowledgable in that area). When it was done, I had an entire Ubuntu drive! I've been trying to get it back to dual booting via GRUB ever since. The problem is, I tried so many solutions, I probably hosed my partitions to the point of no return. I did rebuilds with testdisk and bootrepair. The best I ever got was booting into recovery mode, but it only allowed for clean installs. Now, my Ubuntu partition no longer shows up(I believe it was 30 gig). Bottom line, all my pertinent business data is on the Windows 7 partition. Best case, I would be back to dual booting. Next, getting my data off both partitions. I'm OK with just getting my data off the Window partition or just booting into Windows normally. A heartfelt thanks to anyone willing to take their time to help me. Here's my boot repair URL: [http://paste.ubuntu.com/853211/](http://paste.ubuntu.com/853211/)

Here's my bootinfo data:

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        409,600   454,377,471   453,967,872   7 NTFS / exFAT / HPFS
/dev/sda2         454,377,472   488,183,807    33,806,336   7 NTFS / exFAT / HPFS
/dev/sda3         488,183,808   488,395,119       211,312   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8AEEBD44EEBD28F9                       ntfs       
/dev/sda2        C8308F3C308F310C                       ntfs       RECOVERY
/dev/sda3        50FC-F84C                              vfat       HP_TOOLS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 01 20 00  |.X.MSDOS5.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 18 19 1d  |........?.......|
00000020  70 39 03 00 f0 0f 00 00  00 00 00 00 02 00 00 00  |p9..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 4c f8 fc 50 4e  4f 20 4e 41 4d 45 20 20  |..)L..PNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

ls: reading directory sda1/: Input/output error
```

---

### Post by oldfred on 2012-02-22
You were in an old thread and your problem is not exactly like it, so I moved you to a new thread & edited title. I also added code tags to make boot info script easier to read.

The script did not find an important boot file that normally is in the main or c: drive partition of Windows. In either sda1 or sda2 do you have this file? You show only the first two files that often are in a separate 100MB boot partition that is first or possible second partition after the recovery partition.

Boot files for Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

In either sda1 or sda2 do you have this file and the Windows system folders? 
/Windows/System32/winload.exe

---

### Post by darkod on 2012-02-23
@ericholte
You are not exactly in the right thread because your problem is different, though similar in a way.

I know it might sound harsh and late, but you shouldn't have tried too many things. When something like a partition goes missing happens, of course you will want to try to recover it, but not trying all at once.

It doesn't look very good from your results file. Your best chance is the partition /dev/sda1.

If you boot with the ubunt ucd in live mode, can you open and browse /dev/sda1?

---

### Post by Mark Phelps on 2012-02-23
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

There's also a FREE MS Windows file system recovery app known as Recuva.  You could try that first -- but my experience in MS Windows is you get what you pay for.

Your data ... your money ... your choice.

---

