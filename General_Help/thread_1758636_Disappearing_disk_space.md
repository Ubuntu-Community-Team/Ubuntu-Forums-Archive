---
title: "Disappearing disk space"
date: 2011-05-14
forum: General Help
---

### Post by gunter1959 on 2011-05-14
Using 10.04 on a dual boot laptop, worked fine for over a year.

I noticed that the free space in the partition (75 gig) was shrinking way faster than the file system grew, which at last check was about 15 gig, with only 3.5 gig reported free. (Yes, suspecting trouble I did back up).

This morning, I got presented with a log-in screen not seen before, and upon entering the password got an error message (sorry, didn't write it down, something about Grub being unhappy I think). 

Boote off a live CD, and found that there was no disk space left in the Ubuntu partition, which is what I suspect causes the boot problem from the hard drive.

Then proceeded to check the disk, and this is the output: 


ubuntu@ubuntu:~$ sudo e2fsck -f -v -y /dev/sda5
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  285947 inodes used (5.79%)
    8065 non-contiguous files (2.8%)
     436 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 12184/335/4
19735788 blocks used (100.00%)
       0 bad blocks
       5 large files

  205882 regular files
   37720 directories
      68 character device files
      26 block device files
       4 fifos
     566 links
   42237 symbolic links (34204 fast symbolic links)
       1 socket
--------
  286504 files


Any ideas what's going on? Virus? (there is no anti-vius installed for Ubuntu)

---

### Post by mikewhatever on 2011-05-14
Do you ever empty the Trash? If Trash is not the cause, you'll need to investigate where the the missing disk space is. If you can't use the installed Ubuntu, do it from the Live CD.

-mount the file system
```
sudo mount /dev/sda5 /mnt
```

-use 'du' to get the summary
```
sudo du -s /mnt/* | sort -n
```

If you can use the existing installation, try the following:
```
sudo du -s /* | sort -n
```

---

### Post by drs305 on 2011-05-14
This is a link to a guide about problems similar to yours:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

The three most common things stealing disk space are unemptied trash bins (including root's), large log files, and backups incorrectly created on the system partition instead of another partition.

---

### Post by gunter1959 on 2011-05-15
Thank you!!!

Problem solved: it was Backups Gone Bad. I deleted them from /media/ubuntu/media, and now have the expected 56 G free disk space, and a working computer.

Thanks again, Gunter


> **drs305 said:**
> This is a link to a guide about problems similar to yours:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

The three most common things stealing disk space are unemptied trash bins (including root's), large log files, and backups incorrectly created on the system partition instead of another partition.

---

