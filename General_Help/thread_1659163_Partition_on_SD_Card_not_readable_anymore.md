---
title: "Partition on SD Card not readable anymore"
date: 2011-01-03
forum: General Help
---

### Post by prunus_dulcis on 2011-01-03
Dear all,

today I encountered that the SD-Card holding my 'Home'-Directory would not be recognized anymore when booting. I did some research into the issue to find out what is wrong and I believe, the partition table for some reason got lost yesterday when I shut down the notebook...

Here some hopefully helpful diagnostics - please if you need more information just give me a hint how to get them and I will - I really would love to be able to recover those files again (made an image using partimage) ;)

To me this looks, as if the files are still there but for some reason Ubuntu does not know it? Could it 'just' be the partition table? And how to restore the data access? I'd appreciate any help or advice :)

Ubuntus own Disk Utility gives the following informations:
[IMG]http://www.geoadel.net/files/sd-card-error.png[/IMG]

Mounting the volume does not give me access to the data though, only to the a lost+found folder.


** sudo e2fsck /dev/mmcblk1 -v**
```

e2fsck 1.41.12 (17-May-2010)
Home: clean, 108345/2027648 files, 6754691/8105728 blocks

```sudo e2fsck /dev/mmcblk1 -v -f
```

e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  108345 inodes used (5.34%)
    5864 non-contiguous files (5.4%)
      72 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 12093/1877/1061
 6754691 blocks used (83.33%)
       0 bad blocks
       2 large files

   94141 regular files
   12961 directories
     277 character device files
     263 block device files
     251 fifos
       3 links
     172 symbolic links (151 fast symbolic links)
     271 sockets
--------
  108339 files

```With testdisk only  a deep-search for 'Intel-based' partition tables gives the following output, normal search does not find anything, during the deep search, the following is displayed
[B]
testdisk[/B] during deep search
```

Disk /dev/mmcblk1 - 33 GB / 30 GiB - CHS 1013216 4 16

  Linux                    0   0  1 1013215   3 16   64845824 [Home]
  Linux                    0   0  1 1013215   3 16   64845824 [Home]
  Linux                    0   0  1 1013215   3 16   64845824 [Home]
  Linux                    0   0  1 1013215   3 16   64845824 [Home]
  Linux                    0   0  1 1013215   3 16   64845824 [Home]
  Linux                    0   0  1 1013215   3 16   64845824 [Home]
  Linux                    0   0  1 1013215   3 16   64845824 [Home]
  Linux                    0   0  1 1013215   3 16   64845824 [Home]

```After the search is finished, this screen is displayed:

** testdisk** after deep search is finished
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/mmcblk1 - 33 GB / 30 GiB - CHS 1013216 4 16
     Partition               Start        End    Size in sectors



Structure: Ok.
Keys A: add partition, L: load backup, Enter: to continue

```but no option to restore any data, since it seems it did not find any informations regarding the partition table - adding a partition by hand (Key A) using the suggested values and Linux [83] as values does not result in a partition entry so the only thing I can do is quit... :(

Anyway, it does not look at all like the example output I found for lost partition tables at
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

All the 'Advanced - Filesystem Utils' are not at my disposal since they require a partition table.

**sudo fdisk -lu**   gives the following output regarding the sd-card
```

Disk /dev/mmcblk1: 33.2 GB, 33201061888 bytes
4 heads, 16 sectors/track, 1013216 cylinders, total 64845824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bca24

        Device Boot      Start         End      Blocks   Id  System


```Again this seems to hint at there not being any partition table.

Warm regards and still a happy new year 2011 :p

---

### Post by prunus_dulcis on 2011-01-03
Using gpart
**sudo gpart /dev/mmcblk1** 

I first got a warning
```

* Warning: short read near sector(64845680), 65536 bytes instead of 66048. Skipping...

```and this at least to me not too helpful result:
```

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```But probably one of you knows what that could mean?

All the best!

---

### Post by prunus_dulcis on 2011-01-04
Okay, found another set of informations [here]("http://ubuntuforums.org/showthread.php?t=1606754") and then tried to reconstruct them for my case but I did not get enough informations for recreating the partition table since I do not know where it starts and where it ends...
**sudo fdisk -u /dev/mmcblk1**
```

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c').

Command (m for help): p

Disk /dev/mmcblk1: 33.2 GB, 33201061888 bytes
4 heads, 16 sectors/track, 1013216 cylinders, total 64845824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bca24

        Device Boot      Start         End      Blocks   Id  System


```

Is there a way to guess the necessary informations for the partition table to be recreated?

---

### Post by prunus_dulcis on 2011-01-04
Hm, found another interesting tip here: [http://prefetch.net/blog/index.php/2009/12/20/using-the-linux-parted-utility-to-re-create-a-lost-partition-table/](http://prefetch.net/blog/index.php/2009/12/20/using-the-linux-parted-utility-to-re-create-a-lost-partition-table/)

I used gpart as follows (fonud out, that using -1 as End-value just tells mkpart to use all of it [over here]("http://www.fistagon.us/wp/2010/06/12/warning-the-resulting-partition-is-not-properly-aligned-for-best-performance/"))
***$ sudo parted /dev/mmcblk1***
```

(parted) mkpart primary ext2 1 -1
(parted) p
Model: SD SD (sd/mmc)
Disk /dev/mmcblk1: 33.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End        Size       Type     File system  Flags
 1            1049kB  33.2GB  33.2GB  primary


```But when I try to mount the partition now, Ubuntu throws this error:
```

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/mmcblk1p1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```**dmesg | tail**
```
[55983.621978] EXT2-fs (mmcblk1p1): error: can't find an ext2 filesystem on dev mmcblk1p1.
```
**fdisk -lu mmcblk1** gives the following informations
```

Disk /dev/mmcblk1: 33.2 GB, 33201061888 bytes
255 heads, 63 sectors/track, 4036 cylinders, total 64845824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bca24

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk1p1            2048    64845823    32421888   83  Linux

```
Then, as was suggested [here]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10314803"), I tried
**sudo e2fsck -C0 -p -f -v /dev/mmcblk1**
```

  108345 inodes used (5.34%)
    5864 non-contiguous files (5.4%)
      72 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 12093/1877/1061
 6754691 blocks used (83.33%)
       0 bad blocks
       2 large files

   94141 regular files
   12961 directories
     277 character device files
     263 block device files
     251 fifos
       3 links
     172 symbolic links (151 fast symbolic links)
     271 sockets
--------
  108339 files

```

As you can see, no errors came up... :-?

I really cannot see how to proceed from here - probably will try to create the partition table with fdisk just out of despair and see what comes from it...

---

### Post by prunus_dulcis on 2011-01-04
Okay, now I tried the fdisk way of creating a new partition:

**sudo fdisk  -u /dev/mmcblk1**
```

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c').

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (16-64845823, default 16): 
Using default value 16
Last sector, +sectors or +size{K,M,G} (16-64845823, default 64845823): 
Using default value 64845823

Command (m for help): p

Disk /dev/mmcblk1: 33.2 GB, 33201061888 bytes
4 heads, 16 sectors/track, 1013216 cylinders, total 64845824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bca24

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk1p1              16    64845823    32422904   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```I then tried

**sudo mount -t ext2 /dev/mmcblk1 /media/test/**

This time it mounted but only to display the Lost+Found folder and nothing else.

Interestingly, in nautilus, the sd card is displayed as 'Home' but clicking on it brings this error again:
```

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/**mmcblk1p1**

```Here I notice that it is not actually trying to mount mmcblk1 but  mmcblk1p1 - I have no idea, where that comes from... so I may just be  missing some important background information...

---

### Post by prunus_dulcis on 2011-01-05
Found more informations on how to restore bad superblocks: [http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html)  Did not help me in this case, but may be interesting for my future me or others out there ;)  My best guess right now is, that the partition table also included a never used DOS partition and I cannot figure out the correct order or configuration for the whole table so the ext2 partition remains unaccessible... :(

---

