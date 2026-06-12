---
title: "Did I trash my external HD files?"
date: 2011-09-21
forum: General Help
---

### Post by mrjoeyman on 2011-09-21
I installed the newest 11.04 onto my external HD by mistake, (I just figured this out, I didn't know it at the time). I thought I was installing onto my laptop HD. I decided to do a re-install because everything was so slow. During the re-install I noticed that I was about to install onto the external HD and changed to my laptop drive. Now everything is superfast and great! Except that now I cannot detect my external drive :(  Could someone please tell me how to:

1: Detect the drive and what filesystem is on it, if any is still on it,

2: Find out if everything is deleted that was on it before (I had lots of video files on it), and if all is gone;

3. How to reformat it to use with my new Ubuntu OS.

I am new to Linux so please be gentle.

Here is what I get when I type: sudo fdisk -l :

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cca90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7240    58146816   83  Linux
/dev/sda2            7240        7296      455681    5  Extended
/dev/sda5            7240        7296      455680   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

The large HD is the external drive.

I created a directory in the /media folder and tried to mount the disk to that (I named it External) but I get a lecture on mounting syntax when I try to mount it.


Thanks.

Update:  I just found a program called "Disk Utility". It shows my laptop hard drive and my external hard drive. Unfortunatly it shows my external hard drive as "320 Gb Free" and says it is "Unallocated".  Is this definite confirmation that the drive has been wiped?  And if so, will I need to reformat before I can access it to add files?

---

### Post by patryk77 on 2011-09-22
I have successfully recovered a deleted ext3 partition after someone installed Windows over it on my dad's old laptop using testdisk.

From the terminal:
sudo apt-get install testdisk

It has been a while since I used it, but running:
man testdisk
will give you a lot of info and you can read the documentation online:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Basically, you need to see if it finds your partition, have it write it to disk if it makes sense, mount it and see if you can access the old files on it.

If you have written a lot of data to the disk, you will probably have corrupt files, but there are other tools you can use to try to recover them, the most popular one being foremost:
sudo apt-get install foremost

Any further questions, do post them and I or someone else will try and help out.
Good luck!

---

### Post by Grenage on 2011-09-22
As an amendment to the above, once you have either failed or succeeded in recovering data, you can easily repartition/reformat the drive using gparted.  If it's not installed by default, you can find it in the Software Centre.

---

### Post by mrjoeyman on 2011-09-22
I downloaded testdisk with no problem and did the man testdisk. I looked at the info, and then went to the wiki site and it says to find lost partition or repair file system enter this:

Under Unix/Linux/BSD, you need to be root to run TestDisk (ie. sudo testdisk-6.9/linux/testdisk_static) 
n
My version of testdisk is 6.11 so I entered: sudo testdisk-6.11/linux/testdisk_static

Here is the result: sudo: testdisk-6.11/linux/testdisk_static: command not found

I tried it with 6.1 as version and same result.

Its just a bit over my head but I will be patient, learn and follow directions if you have any.

---

### Post by thefasterblueone on 2011-09-22
Try it with:

```
sudo testdisk
```

---

### Post by Mark Phelps on 2011-09-22
Did you really enter a colon ":" after "sudo", or is that just the way you typed your response?  IF so, do the command again without the colon.

Also, what filesystem was in use on the external drive before you overwrote it? If the drive came preformatted, it was most likely a Windows filesystem, maybe NTFS, maybe FAT32.  Either way, if it was a Windows filesystem, testdisk may not do much for you.

If you find it does not, then post back here and I'll provide instructions on how you can use Windows apps to attempt data recovery from the drive.

---

### Post by patryk77 on 2011-09-22
Actually, I find testdisk does a very good job recovering any kind of partition.

I used it to rebuild a partition table that was overwritten and it recreated all the previous partitions (NTFS, ext3 and swap).

Of course, some of the files were corrupt as the data was overwritten, but overall I can say it did an outstanding job.

[QUOTE=Wiki]TestDisk can

    Fix partition table, recover deleted partition
    Recover FAT32 boot sector from its backup
    Rebuild FAT12/FAT16/FAT32 boot sector
    Fix FAT tables
    Rebuild NTFS boot sector
    Recover NTFS boot sector from its backup
    Fix MFT using MFT mirror
    Locate ext2/ext3/ext4 Backup SuperBlock
    Undelete files from FAT, exFAT, NTFS and ext2 filesystem
    Copy files from deleted FAT, exFAT, NTFS and ext2/ext3/ext4 partitions. 
[/QUOTE]

---

### Post by mrjoeyman on 2011-09-22
Well I thought I tried "sudo testdisk" already but I guess I did not. (I could have left a stray colon in there by mistake). I do actually know that the colon did not belong there. Yay for me! :P

After the program started up it asked me to navigate a little and this is the output I got from it after I chose "Anyalyze":

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

No partition is bootable


Then I clicked on "quick search" and it came up with this:


Should TestDisk search for partition created under Vista ? [Y/N] (answer Yes if
unsure)


Then I said yes and it came up with this:




TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 38912 254 63  625137282 [New Volume]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 320 GB / 298 GiB


Then it asked me to highlight the line up there (with the asterik) and then hit Enter. So I did and this was the output:

Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 38912 254 63  625137282 [New Volume]

[  Quit  ]  [ Write  ]


I am not too sure what this means or what to do next. Here is a readout of the main menu where I may have to go back to and take advantage of some the options it offers:


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sdb - 320 GB / 298 GiB - CHS 38914 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
[ MBR Code ]  Write TestDisk MBR code to first sector
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection






Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.

---

### Post by patryk77 on 2011-09-22
Was that the output from Analyse?

Analyse would be the place to start; it will scan the disk and search for the partitions.

NTFS would be the partition type you should expect, so if Analyse offers to write a partition table with the NTFS partition (and I take it you had just the one partition) you can write it.

This will just overwrite the partition table and not the actual data. Then if you use the Disk Utility it should see it as an NTFS partition.

---

### Post by mrjoeyman on 2011-09-22
I let testdisk write the partition table like it wanted (and you suggested) and then rebooted. Upon reboot, my icon for the drive was on the desktop when it came up. I checked my files and they are all there and working!!!!

I am assuming that I must have installed ubuntu on just part of it or either not at all. I am almost certain that I was running the previous install from there. I must have accessed it somehow and erased the partition table?  I don't understand it all fully yet but it sure was nice of you to take your time and help me. Thanks so much! If I could I would give you a raise!!!:KS:KS:KS

---

### Post by patryk77 on 2011-09-22
No problem.

Hey, this community is what we make of it ;)

It is still possible some files will be corrupted, as when you format in ext{2,3,4} it writes superblocks every x blocks. If your disk had a lot of free space, the likelihood of data being overwritten is lower but I am glad you got most of the data back if not all :)

---

### Post by mrjoeyman on 2011-09-23
Well you were right, some of the videos are jumpy in some places but still watchable. You mentioned another program earlier, is that a program that can "fix" this kind of thing?

---

### Post by patryk77 on 2011-09-23
Generally, no.

foremost is used to make a low-level scan of a partition/disk to search for files based on content, and might give you more corrupt files than anything else; ie it will find 4 bytes identifying a jpg, and say "I found an image", and copy a corrupt file (well, it's not really corrupt, it's just a false positive, or a file that was never really an image).

Once data has been overwritten, it is *very* difficult to recover. You could try a professional recovery service to do it on the hardware level, but they are ridiculously expensive and may not be able to recover the data either.

---

### Post by mrjoeyman on 2011-09-23
Thanks again just wanted to make sure I exhausted all of my options, the last being a little too for over the top for what is on the disk. :P

---

