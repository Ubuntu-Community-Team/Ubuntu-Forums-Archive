---
title: "upgrade to natty fails to boot (/boot in raid5 array)"
date: 2011-05-20
forum: General Help
---

### Post by dr-alves on 2011-05-20
Hi 
 I've struggling with this for a few days, and I've read and searched a lot of google results and forum entries to no avail.

 My box has a raid5 array (mdadm) with everything in it (/boot and /) but swap that is actually spread across the 4 drives.

 I had ubuntu 10.10 installed (amd64) with grub1, when I upgraded to natty (11.04) it automatically installed grub2.

 Well boot fails, it always goes to grub rescue no matter what happens.
 I've installed and reinstalled grub2, and boot always fails with:
 "error: file not found"

 in grub rescue I can see that md0 is actually available, an "ls" to (md0)/boot succeeds but the strange thing is that an "ls" to (md0)/boot/grub prints nonsense, as does an "ls" to (md0)/boot/usr/lib/grub/i386-pc/.

  when I try to load the required modules for boot (linux raid etc) in grub I also always get a "file not found error" (i fsck'd md0, which says everything's fine)

  I have installed the latest version of grub2 and executed grub-install in all four drives.

  Any suggestions?

Cheers
David

---

### Post by linuxinstalledfromhdd on 2011-05-20
you could try:

sudo os-prober sudo update-grub

sudo fdisk -l

And post results

---

### Post by dr-alves on 2011-05-20
thanks for the quick response.

u mean from the livecd env of from the chrooted env?

any how the result of the fdisk (in a livecd env where i installed mdadm, reassembled the array and chrooted into /dev/md0) is:
```


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000507f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244     1951745    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         244      121602   974809088   fd  Linux raid autodetect
/dev/sda5               1         244     1951744   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055c22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1951745    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *         244      121602   974809088   fd  Linux raid autodetect
/dev/sdb5               1         244     1951744   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000077b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         244     1951745    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sdc2   *         244      121602   974809088   fd  Linux raid autodetect
/dev/sdc5               1         244     1951744   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8f37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         244     1951745    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sdd2   *         244      121602   974809088   fd  Linux raid autodetect
/dev/sdd5               1         244     1951744   82  Linux swap / Solaris

Disk /dev/md0: 2994.6 GB, 2994613321728 bytes
2 heads, 4 sectors/track, 731106768 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


```

---

### Post by linuxinstalledfromhdd on 2011-05-20
Stand by while everyone takes a gander.  Hang in there a while.

---

### Post by dr-alves on 2011-05-24
shameless bump!

please help!

---

### Post by dr-alves on 2011-06-17
Are there any recent developments that might help with this problem?
I tried pretty much everything already and just made a purge/reinstall of grub in chroot to no avail.

A very strange thing is that while grub fails to boot with a "error: file not found" md0 (the raid5 volume) is actually present and mounted, as it is possible to see from the grub recovery prompt.

Doing a: "ls (md0)/home/myuser" correctly lists my home
doing a "ls (md0)/boot" correctly lists the boot dir 
BUT "ls (md0)/boot/grub" lists nothing (I think I recall sometime ago it printing nonsense).

While I can still access the info on the server via chroot most services have been dow for weeks as I cannot boot into it. 

Any help would be greatly appreciated.

---

### Post by dr-alves on 2011-06-17
Just to add the result of running bootinfoscript:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (md0)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (md0)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (md0)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (md0)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

md/0: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: /dev/md0 already mounted or MDRaid/md/0 busy
mount: according to mtab, /dev/md0 is mounted on /

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046     3,905,535     3,903,490   5 Extended
/dev/sda5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sda2    *      3,905,536 1,953,523,711 1,949,618,176  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,046     3,905,535     3,903,490   5 Extended
/dev/sdb5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdb2    *      3,905,536 1,953,523,711 1,949,618,176  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,046     3,905,535     3,903,490   5 Extended
/dev/sdc5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdc2    *      3,905,536 1,953,523,711 1,949,618,176  fd Linux raid autodetect


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,046     3,905,535     3,903,490   5 Extended
/dev/sdd5               2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sdd2    *      3,905,536 1,953,523,711 1,949,618,176  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/md0         83d74bfa-d291-446f-afac-6ecb6703463a   ext4       
/dev/md/0        83d74bfa-d291-446f-afac-6ecb6703463a   ext4       
/dev/sda2        35bd1c54-9879-f882-e368-bf24bd0fce41   linux_raid_member 
/dev/sda5        662e7d82-5755-4a2f-8349-968e2a1db0c1   swap       
/dev/sdb2        35bd1c54-9879-f882-e368-bf24bd0fce41   linux_raid_member 
/dev/sdb5        edec0638-d61a-43d2-8466-1f57dc05921c   swap       
/dev/sdc2        35bd1c54-9879-f882-e368-bf24bd0fce41   linux_raid_member 
/dev/sdc5        e9c3ce3a-ce82-4805-8b8b-acf0e3a147ae   swap       
/dev/sdd2        35bd1c54-9879-f882-e368-bf24bd0fce41   linux_raid_member 
/dev/sdd5        050a27da-0eab-4043-911e-e6c121a00bc6   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext4       (rw,errors=remount-ro,commit=0)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 df 5f ff 1f  |........ ...._..|
00000010  01 00 04 00 00 00 00 00  00 00 00 00 ff 1f 47 cd  |..............G.|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 5e 00 20  |........ ....^. |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 44 51  |............. DQ|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 13 6a  |............. .j|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 c8 ca  |............. ..|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 cc 68  |............. .h|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 17 c8  |............. ..|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 79 69  |............. yi|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 a2 c9  |............. ..|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 72 6d  |............. rm|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 a9 cd  |............. ..|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 c7 6c  |............. .l|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 1c cc  |............. ..|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 18 6e  |............. .n|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 c3 ce  |............. ..|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ad 6f  |............. .o|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 76 cf  |............. v.|
00000200

Unknown BootLoader on sdd2

00000000  00 00 c0 07 10 00 c0 07  20 00 c0 07 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 a5 1c  |............. ..|
00000020  01 00 c0 07 11 00 c0 07  20 02 c0 07 00 80 00 20  |........ ...... |
00000030  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d8 87  |............. ..|
00000040  02 00 c0 07 12 00 c0 07  20 04 c0 07 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b6 26  |............. .&|
00000060  03 00 c0 07 13 00 c0 07  20 06 c0 07 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6d 86  |............. m.|
00000080  04 00 c0 07 14 00 c0 07  20 08 c0 07 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 69 24  |............. i$|
000000a0  05 00 c0 07 15 00 c0 07  20 0a c0 07 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b2 84  |............. ..|
000000c0  06 00 c0 07 16 00 c0 07  20 0c c0 07 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 dc 25  |............. .%|
000000e0  07 00 c0 07 17 00 c0 07  20 0e c0 07 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 07 85  |............. ..|
00000100  08 00 c0 07 18 00 c0 07  20 10 c0 07 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d7 21  |............. .!|
00000120  09 00 c0 07 19 00 c0 07  20 12 c0 07 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0c 81  |............. ..|
00000140  0a 00 c0 07 1a 00 c0 07  20 14 c0 07 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 62 20  |............. b |
00000160  0b 00 c0 07 1b 00 c0 07  20 16 c0 07 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b9 80  |............. ..|
00000180  0c 00 c0 07 1c 00 c0 07  20 18 c0 07 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 bd 22  |............. ."|
000001a0  0d 00 c0 07 1d 00 c0 07  20 1a c0 07 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 66 82  |............. f.|
000001c0  0e 00 c0 07 1e 00 c0 07  20 1c c0 07 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 08 23  |............. .#|
000001e0  0f 00 c0 07 1f 00 c0 07  20 1e c0 07 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d3 83  |............. ..|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error



```

---

