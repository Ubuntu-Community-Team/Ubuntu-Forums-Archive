---
title: "Testdisk can't find partition - any hope?"
date: 2011-04-27
forum: General Help
---

### Post by canek1 on 2011-04-27
I borked a 500GB USB hard drive by confusing it with another drive, accidentally trying to erase it, realizing my error and pulling out the cable in panic. Good one! Running Testdisk has found no partitions to fix. Photorec can find most of my files but sorting them out again is going to take weeks. Are there any methods I can use to try and save my folders/file system on the HDD? I'm very much a novice as far as partitions and file systems go, so simple clear instructions or links to easy HOWTOs would be much appreciated. Thanks to all who read this...

---

### Post by TeoBigusGeekus on 2011-04-27
If the partition table has been destroyed, I don't think there's much you can do, sorry.

---

### Post by Buntumatic on 2011-04-27
Actually, there is something to try. If your drive had a single partition then it can be restored just by recreating partition table with fdisk and all the contents should reappear. Worth a try. On the other hand, if you wrote something to this drive after deleting the partition table ... then there is no easy way but Photorec.

---

### Post by dragonfly41 on 2011-04-27
You'll find a lot of advice on data recovery ..

Free utilities such as photorec may recover files .. but you will lose all file names and recovery to the original file hierarchy may not be possible.

Commercial products (at a price) sometimes go further in forensics .. personally I've had very good results from recovermyfiles

[http://www.recovermyfiles.com/](http://www.recovermyfiles.com/)

You can try this product before buying .. to see what files can be recovered. 

But you are advised to take out your disk and run it in slave mode in a USB enclosure plugged into a working windows PC so that it is less stressed and not changed by .. installing recovery programs.

Here are a few other references ..

[http://www.findandmount.com/](http://www.findandmount.com/)


[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Buntumatic on 2011-04-27
Actually, the most safe way to work on it is making a copy of it using dd, mount that copy over loop and leave the actual drive alone.

---

### Post by dragonfly41 on 2011-04-27
> *Actually, the most safe way to work on it is making a copy of it using  dd, mount that copy over loop and leave the actual drive alone*.Probably safer to use clonezilla instead of dd since it is too easy to slip up with the dd command line arguments?
[COLOR=DarkRed]
p.s. If RecoverMyFiles is tried .. as I suggested .. this can only be done on a fully working Windows PC with the corrupted drive plugged in as external USB enclosure.[/COLOR]

---

### Post by Gondrano on 2011-04-27
Help!

I do not know if this is the right thread... thought there is some arguments involved.
Yesterday I made a very silly thing, wanted to repartitioning via  GParted my 320giga ntfs data external hard disk (more than half full)  with ext4, but I end up in a mess. I attach a picture which better  describe where I am now. 

Though the data should be untouched I still does not know how to access it for eventually temporally copy it in a new hard disk.

thanks for advices

ps I think I add a partition (another of the same size) to the only one partition ntfs.[/QUOTE]

---

### Post by Buntumatic on 2011-04-27
> **dragonfly41 said:**
> Probably safer to use clonezilla instead of dd since it is too easy to slip up with the dd command line arguments?
If you say so. I personally like to see what I'm doing, this effectively excludes all nifty frontends. Plus, I'm often working over SSH.

---

### Post by canek1 on 2011-05-03
> **Buntumatic said:**
> Actually, there is something to try. If your drive had a single partition then it can be restored just by recreating partition table with fdisk and all the contents should reappear. Worth a try. On the other hand, if you wrote something to this drive after deleting the partition table ... then there is no easy way but Photorec.

This sounds like the solution I'm looking for. I haven't written anything to the disk, and have in fact managed to recover all my files with photorec. But I still want to recover the partition. Can you tell me how to use fdisk to do this? I've read the fdisk manual and don't see anything about it. 

Maybe this is related... does anybody know what the "add partition" option does in testdisk? Would that help me? Thanks.

---

### Post by Quackers on 2011-05-03
Did you try the deeper search? Have a look here (if you haven't already)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by canek1 on 2011-05-03
> **Quackers said:**
> Did you try the deeper search? Have a look here (if you haven't already)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Yes I did. Thanks. I'm checking out your link now. So far, I haven't found anything that directly answers my question, but it's a very useful resource all the same.

---

### Post by oldfred on 2011-05-03
Some more info.

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

this user had similar issues and found a couple of alternatives that worked a bit better.
See post #22 for results from several recovery tools.
[http://ubuntuforums.org/showthread.php?t=1742220](http://ubuntuforums.org/showthread.php?t=1742220)

---

### Post by canek1 on 2011-05-06
> **oldfred said:**
> Some more info.

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

this user had similar issues and found a couple of alternatives that worked a bit better.
See post #22 for results from several recovery tools.
[http://ubuntuforums.org/showthread.php?t=1742220](http://ubuntuforums.org/showthread.php?t=1742220)

Thanks oldfred.  Unfortunately, the post re. using Hiren's Boot CD didn't work out for me. Diskgenius and the other programs found no files or partitions (even though I've already rescued most of the files.) At least, those links on what to do after photorec are going to be very useful!

I'll just make one last request before getting down to sorting out 50,000 rescued files... does anyone know how to recreate a partition using fdisk, as an earlier commenter on this thread suggested?

---

### Post by oldfred on 2011-05-06
Do you have the exact sector starts & ends for your partitions? Perhaps a printout somewhere. A run of boot info script?

There seem to be several tools to use at command line and since DOS days I have not used them. fdisk, sfdisk, parted

If you run this I assume you get nothing since testdisk does not find anything.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sdb > PTsdb.txt


Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by canek1 on 2011-05-10
oldfred, i don't have the starts and ends for the partition. I know the size of the drive and (I believe) there was only one partition on the drive. Boot_info_script gives me this:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,064   976,768,002   c W95 FAT32 (LBA)

Does this make any sense to you? It also says (of this drive):

Mounting failed:
mount: unknown filesystem type ''

Sorry for the slowness of my responses. I"m trying to finish a thesis at the same time as fix my drive! I do appreciate your excellent advice so far.

---

### Post by Buntumatic on 2011-05-10
Basically, partition table is just a few bytes on MBR. If I recall correctly first 446 B out of 512 B is boot code, rest is the partition table. It can hold information for 4 primary partitions. By modifying primary partitions you are not affecting the actual data on drive in any way.
Now, the partition table was created with fdisk or similar tool. Something happened to it, you deleted it. All you need to do is repeat the partition creation process. I'd try and create one partition with default start and end and see if it works. You may do it with DOS fdisk, I think Linux fdisk may not have same defaults.

---

### Post by LostFarmer on 2011-05-10
The fdisk output {/dev/sdc1    *             63   976,768,064   976,768,002   c W95 FAT32 (LBA)}  shows one large partition of type FAT32.  If the partition was indeed FAT32 , rerun 'testdisk' on about the 3rd screen select '**Advanced**' . Next window hilight the partition and at bottom select boot, next **rebuild bs.** (This will not work if the partition was formated.)

My be if you post what you did to get the partition deleted would be good for use to know.
If you formated the drive that would make a big difference on what might work.

---

### Post by canek1 on 2011-05-10
I messed up the drive by trying to format a USB key with Ubuntu Startup Disk creator. I accidentally selected this 500GB external drive instead of the USB key (I was tired.) After about three seconds, I realized my error and pulled out the USB cable. Since then, I haven't written anything to the drive, except... after being unable to find the old partition record with Testdisk, Parted, or any other program, I selected "rebuild MBR" using the Window's program Discgenius. 

I assume that the partition table I'm seeing now with fdisk is a result of this action, ie. created by Discgenius. As far as I can tell, all the files are still intact, since Photorec and Foremost have found thousands of them. 

So fdisk is telling me there is a partition table. To my limited knowledge it looks right. But I can't mount the drive and Boot_info_script tells me "Unknown filesystem type."

---

### Post by Buntumatic on 2011-05-10
Now when you described it in more detail it's quite clear you destroyed File Allocation Table. That explains why Testdisk can't find the partition. I don't think there is something you can do about it now.

---

### Post by LostFarmer on 2011-05-10
To mount and read a partition there are several required items.  
1) listed in the MBR/Master Partition Table
2)Volume Boot Record.  the first sector of partition, on fat32 there is a back up at about sector 6
3)For Fat32- The File Allocation Table 'FAT', start about sector 26, with a backup right after the primary. The size of the FAT will depend on the partition size and block size.

After the FATs is normally the root directory.

Formatting will rewrite the VBR , zero out the FAT's and root directory.

The VBR contain some very important information. 
1) block size
2) location and size of FAT
3) location of root directory
4) partition size
5) partition type

A guess:  'testdisk' to rebuild the VBR must figure out the block size (do not have any idea how), find the primary or secondary FAT, find root directory. 

If both fats  have been zeroed out then what you have recovered is it.

When 'testdisk' tries to find a partition, I think it mostly searches for a VBR data and not for the FAT.  Linux nor NTFS uses FATS.

---

### Post by dragonfly41 on 2011-05-10
Just to stir the pot ..

I'm not sure if you have windows running on another partition or if you can plug in your external drive into a working windows PC for recovery ..

but you might try ... [http://www.ufsexplorer.com/download.php](http://www.ufsexplorer.com/download.php) .. try it in demo mode first before buying!


If you only have ubuntu you could try installing gpart .. I just found it recently after searching around.   Not to be confused with gparted.


**[COLOR=DimGray]sudo gpart /dev/sdc[/COLOR]**

---

### Post by oldfred on 2011-05-10
You could try running chkdsk on the drive. Chkdsk will take forever on a large drive.  If testdisk has not found anything I would not be too hopeful. I would make sure I had the files backed up first as chkdsk may rebuild a blank drive and you may lose more. 

Chkdsk also does not repair everything on one pass. Often several passes are required.

FAT is really only recommended for compatibility with other devices. It cannot store large files over 4GB and has no journal to speed up recovery.

---

### Post by canek1 on 2011-05-24
This is just to round out the thread for anyone else who lands here with the same problem... I wasn't able to recover the FAT despite all the advice. I assume I erased it for good either when I originally reformatted the disc or when I later tried to rebuild the MBR with discgenius. 

I seemed to have rescued all my files using a combination of photorec and scalpel. It's a bit tedious because neither program rescues all file types and with scalpel I had to do some wierd editing of the config file to get my OpenOffice files. None of the files have titles, and there are tons of duplicates but I spent a day indexing them with Google Desktop (tracker was a total bust) and have so far been able to find everything I needed.

Thanks very much to all contributors to this thread. Wish I could mark it solved, but it could have been worse. :-).

---

### Post by linuxinstalledfromhdd on 2011-05-24
you know how much money sandisk would have charged you per hour to do that for you? :) lol

---

