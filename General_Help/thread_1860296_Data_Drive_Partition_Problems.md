---
title: "Data Drive Partition Problems"
date: 2011-10-14
forum: General Help
---

### Post by bcollier on 2011-10-14
I just added a raid drive (using motherboard raid ASUS P5Q Pro Turbo) to Ubuntu 11.10, and I am having a very strange problem with it.  When I boot it doesn't show up as a drive, when I go to gparted there is a red exclamation point on it (see picture), and the information says:

e2label:  No such file or directory while trying to open /dev/mapper etc

Couldn't find valud filesystem superblock

Unable to read contents of the file system!  (see picture for more details).

What is strange is that I can fix it by doing something very strange.
1) Manage Flags
2) Uncheck raid (if it was previously checked) or check raid (if it was unchecked)

Boom, the ! goes away, no problems in information, and the drive automatically mounts in the file system.  All of the data on the drive is good to go, a copy of the check is below.  The drives are 4 brand new 1 TB hard drives running raid 0 (I analyze large data sets).  

I would appreciate help on this, it creates problems to have to manually do this every time.  It is such a strange fix, that it seems like a bug.  I will plan on reporting a bug on this if I don't hear back.  Thank you!

I should mention the drive is formatted as ext4

GParted 0.8.1 --enable-libparted-dmraid
 Libparted 2.3
    **Check and repair file system (ext4) on /dev/mapper/isw_dhigihjdae_BlueGene4T1**  00:00:51    ( SUCCESS )             calibrate /dev/mapper/isw_dhigihjdae_BlueGene4T1  00:00:00    ( SUCCESS )             [I]path: /dev/mapper/isw_dhigihjdae_BlueGene4T1
start: 2048
end: 7814080511
size: 7814078464 (3.64 TiB)[/I]          check file system on /dev/mapper/isw_dhigihjdae_BlueGene4T1 for errors and (if possible) fix them  00:00:51    ( SUCCESS )             ***e2fsck -f -y -v /dev/mapper/isw_dhigihjdae_BlueGene4T1***             [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      11 inodes used (0.00%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 1
15377150 blocks used (1.57%)
       0 bad blocks
       1 large file

       0 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       2 files
[/I]       [I]e2fsck 1.41.14 (22-Dec-2010)
[/I]             grow file system to fill the partition  00:00:00    ( SUCCESS )             ***resize2fs /dev/mapper/isw_dhigihjdae_BlueGene4T1***             [I]resize2fs 1.41.14 (22-Dec-2010)
The filesystem is already 976759808 blocks long.  Nothing to do![/I]

---

### Post by dcstar on 2011-10-14
> **bcollier said:**
> I just added a raid drive (using motherboard raid ASUS P5Q Pro Turbo) to Ubuntu 11.10, and I am having a very strange problem with it.  When I boot it doesn't show up as a drive, when I go to gparted there is a red exclamation point on it (see picture), and the information says:
.........

I have seen posts that say you have to manually fix the /etc/fstab file (and possibly others) when using RAID, the install process does not set them up correctly.

Do a web search for similar problems.

I hope you are aware that using RAID-0 means that if one of your array disks fails, you lose the data on** all** the other disks.

---

