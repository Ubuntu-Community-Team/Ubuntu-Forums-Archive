---
title: "Disk sizes inconsistent"
date: 2010-06-17
forum: General Help
---

### Post by hansum_rahul on 2010-06-17
When I do consistency check on my /dev/sda1 I get this:

[COLOR="Red"] Warning!
 ========

 Partition 2 is 20201MB, but the file system is 14756MB.
[/COLOR]
I understand that my blocks are allocated but not formatted?

My fdisk is like this:

[COLOR="red"]
Disk /dev/sda: 80 GB, 80023749120 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1047     8409996   83  Linux
/dev/sda2            1048        3503    19719787   83  Linux
/dev/sda3            3504        9729    50002312    f  Extended LBA
/dev/sda5            3504        9598    48950055   83  Linux
/dev/sda6            9599        9729     1044225   82  Linux swap
[/COLOR]

When I check in gparted, I get this
[COLOR="red"]
GParted 0.3.5

Libparted 1.7.1

Check and repair filesystem (ext3) on /dev/sda1  00:34    ( SUCCES )
    	
calibrate /dev/sda1  00:00    ( SUCCES )
    	
path: /dev/sda1
start: 63
end: 16820054
size: 16819992 (8.02 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:34    ( SUCCES )
    	
e2fsck -f -y -v /dev/sda1
    	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

6771 inodes used (1.29%)
153 non-contiguous inodes (2.3%)
# of inodes with ind/dind/tind blocks: 1122/21/1
1679763 blocks used (79.89%)
0 bad blocks
2 large files

5636 regular files
1039 directories
0 character device files
0 block device files
0 fifos
0 links
85 symbolic links (3 fast symbolic links)
2 sockets
--------
6762 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( SUCCES )
    	
resize2fs /dev/sda1
    	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 2102499 blocks long. Nothing to do!


========================================
[/COLOR]

Also gparted reports free space  [IMG]http://ubuntuforums.org/attachment.php?attachmentid=160713&stc=1&d=1276758611[/IMG] much more than what I see by df.

Here is a output from
df /dev/sda? -h

[COLOR="red"]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.9G  6.3G  1.3G  84% /media/disk
/dev/sda2              14G   14G  350M  98% /
/dev/sda5              47G   45G  418M 100% /media/Entertainment
udev                  505M   56K  505M   1% /dev
[/COLOR]


How should  resolve this issue?

Btw my system is this:
Linux rahul-desktop 2.6.24-27-generic #1 SMP PREEMPT Tue Jun 15 19:38:37 IST 2010 i686 GNU/Linux

---

### Post by bumanie on 2010-06-17
The reason why you are getting weird/inconsistent messages about the hard drive is because every partition is nearly full, especially /dev/sda2 and /dev/sda5. When filesystems get as full as that, they give strange errors. You really need a new or extra hard drive to allow more storage space. In the meantime, you can do this from your /home directory (which I assume is part of /dev/sda2) in terminal > sudo apt-get autoclean and then > sudo apt-get clean. This should clear out some space. Also /boot is very large and very full also - most boot partitions are only about 100mb for bootloader information - what have you been saving in there? /dev/sda5 is also very full.
You should carefully read [this]("http://gparted.sourceforge.net/docs/help-manual/C/gparted.html") after installing another or larger hard drive to learn how to move/copy partitions etc.

---

### Post by hansum_rahul on 2010-06-17
Well I have cleaned up space and I don't think having disk "almost" full can trigger something like that.

It is a bug. It was triggered once when I was resizing partitions. I wanted to take space off /dev/sda1 and add it to /dev/sda2.

Gparted has exited with an error. However, I thought it was nothing serious and here I am!

About 2-3 GB of my space is wasted.

---

### Post by hansum_rahul on 2010-06-20
I guess the bug was in **resize2fs** since it has reclaimed the free lost space after I booted with a new Jaunty (10.04) Disk and did a disk check.

---

