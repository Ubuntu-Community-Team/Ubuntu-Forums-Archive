---
title: "HPFS/NTFS won't mount"
date: 2010-10-20
forum: General Help
---

### Post by Troilus98 on 2010-10-20
Recently installed ubuntu 10.10 and rather like it but been trying to setup and configure everything so its a feasible alternate OS.  

I have a problem where one of my hard drives doesnt show up in places.

The drive works fine in windows.

The information provided to me by Disk Utility says:

Model: ATA WDC WD 10EADS-00L5B1
Partitioning: Master Boot Record
Device: /dev/sdb
Partition Type: HPFS/NTFS (0x07)


Now i have a total of 4 drives, windows 7 on one, linux on one, and 2 storage.  Linux recognizes my main windows drive and my 2 TB storage drive, but not this one for some reason.  I assume it has to do with the partition type?  Disk utility just shows its parition bar image as 'unknown' so yeah.  Now there is one error during boot related to this but i can't read it fast enough to remember it all, all i see is the sdb label real quick.

Any suggestions?

---

### Post by P4man on 2010-10-20
You can see the messages from the boot process by typing

```
dmesg
```

in a terminal. (or system > administration > log file viewer > dmesg)

BTW, is it /dev/sdb or  /dev/sdb**1** ? What does 

```
sudo fdisk -l
```

report? (run that in a terminal)

---

### Post by Troilus98 on 2010-10-21
fdisk -l information, and its the sdb 1 tb drive thats not working correctly.  Still trying to read thru the boot up log to find relevant error message during boot.


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9d75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244     1951744   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2             244       48642   388756481    5  Extended
/dev/sda5             244       48642   388756480   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10a76bdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2      121601   976751968+   7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      266306  2147483647+  ee  GPT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x171001d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488383939+   7  HPFS/NTFS

---

### Post by P4man on 2010-10-21
Are you *sure* its sdb, the 1TB drive, and not sdc, the 2TB drive that you cant access?

If you are sure, then report what happens when you type

```
sudo mkdir /media/1tb
sudo mount /dev/sdb1 /media/1tb
```

If you get no error, browse to /media/1tb and verify if you can access the filesystem.

BTW, you think you got enough storage in there :o

---

### Post by srs5694 on 2010-10-21
Two more suggestions:


[list]
[*]Type "sudo blkid /dev/sdb1" and report the results (if any). This utility *should* identify the partition as being of type NTFS. If it doesn't print any results, then that means that Linux can't identify the filesystem on the partition. (Note that fdisk just reports the partition type code, which can be set to something other than what the partition actually contains, much like a label on an office file cabinet drawer.) This won't fix anything, but it could provide useful diagnostic information.
[*]In Windows, run the CHKDSK utility on the partition in question. Keep doing this until the utility reports no errors. This could fix the problem, but I can't say that's anywhere near certain. It *is* certainly worth trying, though.
[/list]

---

### Post by Troilus98 on 2010-10-21
Ok

trying to mount sdb1 to the folder u had me create, reports "Segmentation fault"

and to the other commenter

sudo blkid for sdb1 says "Segmentation fault"

running chkdsk in windows on that drive said it found and fixed errors (I did that before trying in linux again).  Maybe ill try it over again.

So i guess the question now is what is segmentation fault, and how do i fix it

---

### Post by Troilus98 on 2010-10-21
Also, would it matter to linux if this 1 TB drive is a bootable windows drive? I use windows 7 64bit off of the 500gig drive, but the 1tb has w7 32bit, except i removed it from the boot loader in windows a while back.

---

### Post by Troilus98 on 2010-10-22
I noticed it says that sdb starts on 2 and ends on xxx.  But every other disk starts on 1 and ends on xxx, even with their multiple partitions, and sdb only has one partition.  Is that problematic?

---

### Post by P4man on 2010-10-22
This is a wild guess. Googling I came across this (fixed) bug report:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/428318](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/428318)

The issue looks different, these people had 2 conflicting filesystems on their harddisk which made the drive unmountable, but blkid gave a correct response. Now Im guessing you may have that same problem, but the "fix" released for this causes your segfaults.

A few things to try:

```
sudo blkid -p /dev/sdb1
```

If that segfaults, maybe you could boot an older ubuntu CD (9.1 or older) and try the blkid again and see if it reports "ambivalent result ".

If you dont have an old live cd, maybe you can run this command (snatched from the bug report):
```

dd if=/dev/sdb1 of=bootsector bs=512 count=1
hexdump -C bootsector
```

and post the output. If it turns out you have also some old windows remainders there, you could try the solution suggested in that thread by zeroing out the first sector. Be very careful doing that, and I wouldnt  do that if you dont have backups of your files.

OTOH, if you have ample free space, Id just copy the files to another drive, and repartition and reformat the drive.

---

### Post by matt_symes on 2010-10-22
Hi

Might be worth running ntfsfix on the drive. It might have some issue. I have never used it so....

> DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.


Kind regards.

---

### Post by srs5694 on 2010-10-22
If you've run CHKDSK in Windows (repeatedly, until it reports no errors), then you should definitely try accessing the disk again in Linux. That's the point of the CHKDSK exercise -- to fix the disk. *Do not* run ntfsfix in Linux after running CHKDSK in Windows; ntfsfix is a very very basic NTFS maintenance tool, and its main function is to set it so that Windows will run CHKDSK on the disk when it reboots. It's not likely to have a positive effect in this situation unless you reboot to Windows first, and then the effect will be no better than running CHKDSK manually.

A segmentation fault usually indicates a program bug -- the program has attempted to access memory to which it doesn't have access or is otherwise doing something wrong. In this case, it could mean that something about the NTFS partition is odd in a way that the blkid programmers didn't anticipate. For instance, blkid might be loading a value from disk and attempting to use it as an index into an array. If the structures are valid, this might work; but if not, the index might be ridiculous, thus causing a segmentation fault. (That's just a speculative example; I don't mean to suggest that I know this is what's happening in this specific case.)

---

### Post by Troilus98 on 2010-10-22
> **P4man said:**
> 

A few things to try:

```
sudo blkid -p /dev/sdb1
```If that segfaults, maybe you could boot an older ubuntu CD (9.1 or older) and try the blkid again and see if it reports "ambivalent result ".

If you dont have an old live cd, maybe you can run this command (snatched from the bug report):
```

dd if=/dev/sdb1 of=bootsector bs=512 count=1
hexdump -C bootsector
```and post the output. If it turns out you have also some old windows remainders there, you could try the solution suggested in that thread by zeroing out the first sector. Be very careful doing that, and I wouldnt  do that if you dont have backups of your files.

OTOH, if you have ample free space, Id just copy the files to another drive, and repartition and reformat the drive.

first suggestion gives segfault.

second suggestion output:

troilus@Troilus-Linux:~$ sudo dd if=/dev/sdb1 of=bootsector bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.459998 s, 1.1 kB/s
troilus@Troilus-Linux:~$ hexdump -C bootsector
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 3f 00 00  |........?....?..|
00000020  00 00 00 00 80 00 80 00  c0 1a 70 74 00 00 00 00  |..........pt....|
00000030  00 00 0c 00 00 00 00 00  ac 01 47 07 00 00 00 00  |..........G.....|
00000040  f6 00 00 00 01 00 00 00  8a 42 8c 80 58 8c 80 54  |.........B..X..T|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200


I could just copy its stuff to another drive, reformat, and copy back see if that fixes.  I prefer to try and figure out and fix any problems i find first, instead of the bulldozer solution.  We'll see how frustrated i get.

---

### Post by Troilus98 on 2010-10-22
> **srs5694 said:**
> If you've run CHKDSK in Windows (repeatedly, until it reports no errors), then you should definitely try accessing the disk again in Linux. That's the point of the CHKDSK exercise -- to fix the disk. *Do not* run ntfsfix in Linux after running CHKDSK in Windows; ntfsfix is a very very basic NTFS maintenance tool, and its main function is to set it so that Windows will run CHKDSK on the disk when it reboots. It's not likely to have a positive effect in this situation unless you reboot to Windows first, and then the effect will be no better than running CHKDSK manually.



Ran it once 2 days ago, it found and fixed errors. I've run it like 3 more times since then and no errors found.

---

