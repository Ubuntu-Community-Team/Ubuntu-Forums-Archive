---
title: "GParted help required; Error while reading block at sector 142257725"
date: 2010-01-06
forum: General Help
---

### Post by RafiB on 2010-01-06
Hi,
I've been trying to re-arrange the partitions on my hard drive. I tried to move /dev/sda5 to the right, so that I could pull an empty (unformatted) partition out of my Ubuntu extended partition.

It worked until a certain stage, when the process halted.
I have the details copied and pasted below. Please help me, I really want this to work.

Thanks,
Rafi

p.s. If any extra information is required, just ask :)

> [SIZE=2][COLOR=Red]GParted 0.3.8

Libparted 1.8.9

[/COLOR][/SIZE]    [SIZE=2][COLOR=Red]**Move /dev/sda5 to the right**  00:05:39    ( ERROR ) [/COLOR][/SIZE]       [SIZE=2][COLOR=Red] calibrate /dev/sda5  00:00:01    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red][I]path: /dev/sda5
start: 117194301
end: 154336517
size: 37142217 (17.71 GiB)[/I][/COLOR][/SIZE]         [SIZE=2][COLOR=Red] calculate new size and position of /dev/sda5  00:00:00    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red][I]requested start: 151396623
requested end: 188538839
requested size: 37142217 (17.71 GiB)[/I][/COLOR][/SIZE]       [SIZE=2][COLOR=Red][I]new start: 151396560
new end: 188538839
new size: 37142280 (17.71 GiB)[/I][/COLOR][/SIZE]         [SIZE=2][COLOR=Red] check filesystem on /dev/sda5 for errors and (if possible) fix them  00:01:06    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]***e2fsck -f -y -v /dev/sda5***[/COLOR][/SIZE]         [SIZE=2][COLOR=Red][I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   20094 inodes used (1.73%)
    1740 non-contiguous inodes (8.7%)
         # of inodes with ind/dind/tind blocks: 1867/338/1
 3796269 blocks used (81.77%)
       0 bad blocks
       3 large files

   16655 regular files
    3106 directories
       0 character device files
       0 block device files
       0 fifos
       1 link
     321 symbolic links (69 fast symbolic links)
       3 sockets
--------
   20086 files
[/I][/COLOR][/SIZE]       [SIZE=2][COLOR=Red][I]e2fsck 1.41.3 (12-Oct-2008)
[/I][/COLOR][/SIZE]            [SIZE=2][COLOR=Red] move filesystem to the right  00:04:32    ( ERROR ) [/COLOR][/SIZE]       [SIZE=2][COLOR=Red] perform readonly test  00:04:32    ( ERROR ) [/COLOR][/SIZE]       [SIZE=2][COLOR=Red] using internal algorithm [/COLOR][/SIZE]     [SIZE=2][COLOR=Red] read 37142217 sectors [/COLOR][/SIZE]     [SIZE=2][COLOR=Red] finding optimal blocksize [/COLOR][/SIZE]       [SIZE=2][COLOR=Red] read 32768 sectors using a blocksize of 128 sectors  00:00:02    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*32768 of 32768 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*1.3769 seconds*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] read 32768 sectors using a blocksize of 256 sectors  00:00:01    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*32768 of 32768 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*0.989461 seconds*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] read 32768 sectors using a blocksize of 512 sectors  00:00:01    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*32768 of 32768 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*0.902992 seconds*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] read 32768 sectors using a blocksize of 1024 sectors  00:00:01    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*32768 of 32768 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*0.898978 seconds*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] read 32768 sectors using a blocksize of 2048 sectors  00:00:00    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*32768 of 32768 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*0.771132 seconds*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] read 32768 sectors using a blocksize of 4096 sectors  00:00:01    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*32768 of 32768 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*0.694476 seconds*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] read 32768 sectors using a blocksize of 8192 sectors  00:00:01    ( SUCCESS ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*32768 of 32768 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*0.700464 seconds*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] optimal blocksize is 4096 sectors (2.00 MiB) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red] read 36912841 sectors using a blocksize of 4096 sectors  00:04:25    ( ERROR ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*11845321 of 36912841 read*[/COLOR][/SIZE]       [SIZE=2][COLOR=Red]*Error while reading block at sector 142257725*[/COLOR][/SIZE]         [SIZE=2][COLOR=Red] 12074697 sectors read [/COLOR][/SIZE]           [SIZE=2][COLOR=Red] libparted messages    ( INFO ) [/COLOR][/SIZE]        [SIZE=2][COLOR=Red]*Input/output error during read on /dev/sda*[/COLOR][/SIZE]          [SIZE=2][COLOR=Red]
========================================[/COLOR][/SIZE][SIZE=2][COLOR=Red][/COLOR][/SIZE]

---

### Post by dcstar on 2010-01-07
> **RafiB said:**
> Hi,
I've been trying to re-arrange the partitions on my hard drive. I tried to move /dev/sda5 to the right, so that I could pull an empty (unformatted) partition out of my Ubuntu extended partition.

It worked until a certain stage, when the process halted.
I have the details copied and pasted below. Please help me, I really want this to work.

Thanks,
Rafi

p.s. If any extra information is required, just ask :)


You have a bad block on your hard drive, it's as simple as that.

---

### Post by RafiB on 2010-01-08
Is there anything that I can do about that?

---

### Post by louieb on 2010-01-08
If the partition is ext3 you can use partimage - create an image file - delete, re-add the the partition in the new location - restore the image. I've done that to get around Gparted not being able to copy partitons before.

Partimage does not work for ext4 partitions. guess you could use tar or some other backup/restore  program and do the same thing.

---

### Post by RafiB on 2010-01-08
I tried using partimage; it returns two consecutive errors. The first is:
```

e2fsck found errors on the file system.

```
And the second is:
```

Can't read bitmap block 0 from image

```

---

