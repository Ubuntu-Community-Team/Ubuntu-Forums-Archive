---
title: "Home partition has disappeared! TestDisk can see it though"
date: 2012-07-20
forum: General Help
---

### Post by Steve Francis on 2012-07-20
I have a dual boot XP/Ubuntu system, which suffered a momentary power glitch *whilst I was using XP*.

(XP now boots up really slowly and the File Manager hangs.)

I then booted up in Ubuntu and found that my home partition ( /dev/sda3) had been damaged. All my desktop settings and documents had disappeared!

I have managed to get the system files working correctly but a new home folder has been created and I can't find my old files

Ubuntu's Disk Utility reported the partition type on /dev/sda3 as 'unknown'. TestDisk reported that sda3 had the FAT file system (I'm sure it wasn't set up like that!) so I've used Disk Utility to change it to Partition Type Linux (0x83).

Is there any way I can recover the original home partition can still be rescued and point the boot up towards it?

---

### Post by oldfred on 2012-07-20
If it is back to ext4 and testdisk does see it ok, then you may just need fsck.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Also if Windows is slow it can be it needs chkdsk or that it is getting full. NTFS partitions work best with 30% free, slow at 20% and will crawl at 10% free.

---

### Post by Steve Francis on 2012-07-20
> **oldfred said:**
> #e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

LiveCD doesn't recognise /dev/sda3 as ext4. Disk Utility just shows the partition as unknown. :(

The e2fsck command returns the following:
[FONT=Courier New]ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

    8340 inodes used (0.61%)
     196 non-contiguous files (2.4%)
       8 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 8265/57
 4464947 blocks used (81.86%)
       0 bad blocks
       2 large files

    6262 regular files
    2062 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       7 symbolic links (7 fast symbolic links)
       0 sockets
--------
    8331 files[/FONT]


Thanks for your suggestion OldFred. Anything else that I can try now?

---

### Post by oldfred on 2012-07-20
It looks like e2fsck ran?

Run the BootInfo from this and post link. Not looking for any of the boot issues but it also shows partition info that may tell something.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Steve Francis on 2012-07-21
> **oldfred said:**
> It looks like e2fsck ran?

Run the BootInfo from this and post link. Not looking for any of the boot issues but it also shows partition info that may tell something.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Thanks. I'm away from p.c. for 7 days. Will try again when I get back home and report here again. Appreciate the help. All the best.

---

### Post by Steve Francis on 2012-07-28
Back home and back trying to rescue the situation

> **oldfred said:**
> Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Here's the link:

[http://paste.ubuntu.com/1115852/](http://paste.ubuntu.com/1115852/)

My original '/home' partition (/dev/sda3) is being reported as FAT32! (I'm sure that's not right. I would have formatted it as a Linux partition.)

The only thing I can think is that I tried to recover some files using Photorec and wrote some recovered files to the damaged partition before cancelling the operation.

Is there any way I can force Ubuntu to change the partition back to an 'ext' one?

---

### Post by oldfred on 2012-07-28
If it was reformated, I am not sure what damage that might do.

You can use Disk Utility to change to ext4. Your fstab says during install it was ext4.

Testdisk may show it as the old partition and and let you recover the old partition, but whether data is ok or not is still a question.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Steve Francis on 2012-07-28
> **oldfred said:**
> If it was reformated, I am not sure what damage that might do.

You can use Disk Utility to change to ext4. Your fstab says during install it was ext4.

Testdisk may show it as the old partition and and let you recover the old partition, but whether data is ok or not is still a question.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Thanks oldfred!

I didn't reformat the disk so hopefully there is something there that can be saved.

Will try your suggestions and report back. Here goes...

---

### Post by Steve Francis on 2012-07-28
> **Steve Francis said:**
> Will try your suggestions and report back.

Used Disk Utility to change file structure to Linux. Ran testdisk which could locate the missing directory structure (but couldn't list the files). Used testdisk to write the new partition table.

Loaded Boot Repair. The new link is here:

[http://paste.ubuntu.com/1116122/](http://paste.ubuntu.com/1116122/)

Partition has changed to /dev/sda2/. Boot sector type is reported as FAT32 :( but partition info now shows /dev/sda2 to be Linux.

---

### Post by oldfred on 2012-07-28
I do not think Linux uses Boot sector for anything. But script is seeing partition as FAT not ext4. I think it was formated or else that info would not be there. Internal structures of FAT and ext4 are different and that does not look like it has been updated and may not be able to be?

Did not testdisk recover partition as ext4?

If you have data not well backed up, you may be able to recover some data with photorec. It can be a long slow process as it just scans drive for anything that looks like a file. It cannot recover name, just extensions based on what it thinks it finds. I used it to recover some text files that I had updated many times since backup. It found all the old copies and I had to do a lot of grepping & comparing to get most of data back. Never was sure if I found last saved version.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Steve Francis on 2012-07-29
> **oldfred said:**
> Did not testdisk recover partition as ext4?

It reports it as Linux partition but does not say the file structure. It's a shame because testdisk can see the old directory structure but cannot find files (using the press 'P' command)

> **oldfred said:**
> If you have data not well backed up, you may be able to recover some data with photorec.

I've done this overnight and it seems to have recovered many files. Will have to sort through them when the system is back up and running.

I have got the p.c. booting from the Windows partition by following the instructions here:
[https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Remove-Grub-back-to-Windows-only-](https://sites.google.com/site/easylinuxtipsproject/grub#TOC-Remove-Grub-back-to-Windows-only-)

I am now going to try and reinstall Ubuntu on the other Linux partitions.

---

### Post by Steve Francis on 2012-08-01
Thanks to oldfred for providing support on this subject.

I re-installed Ubuntu so at least I'm up and running again.

I am now wading through my photorec output files to try and gather some key lost files.

Rule 1 - Make frequent back ups
Rule 2 - Remember Rule 1

---

