---
title: "Data Recovery"
date: 2010-04-03
forum: General Help
---

### Post by ranjank on 2010-04-03
Yesterday my ubuntu 9.10 got corrupted , As I don't know to repair corrupted ubuntu , reinstalled it . I lost about 90-100 GB of data . My question is how can i recover that data?

---

### Post by ranjank on 2010-04-04
No solutions ?

---

### Post by AlexFox on 2010-04-04
AFAIK, it's very difficult to recover data from an EXT3/4 partition. Also, because you've reinstalled, there is a good chance that you've over written the data already. You can try and give this app a bash, haven't tried it my self

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

---

### Post by Directive 4 on 2010-04-04
testdisk

---

### Post by mickObrian on 2010-04-04
I'd recommend using the LiveCD next time something like that happens before you re-install as you may have overwritten the data and it makes it a lot harder to get back, in the LiveCD you may at least be able to gather your files before doing a re-install if necessary.

---

### Post by SPr on 2010-04-04
It's probably too late but try photorec on [SysRescueCD](http://www.sysresccd.org/). Burn the iso to a cd and boot the computer with the CD.

DO NOT use the computer with the data you want to recover because that data could easily be overwritten.
DO NOT save the recovered data on the HDD from which it is being recovered. It could easily overwrite that which you want to recover. 

External HDDs are cheap so I suggest you buy one and keep backups of important data as well as back ups of the OS.

---

### Post by brcre on 2010-04-04
Agreed, you should not have continued using the same disk to recover your system if your intent was getting the data back.

I purchased EaseUS software [http://www.easeus.com/](http://www.easeus.com/) in an attempt to try and recover data from a 500G drive that was originally EXT3 and was formatted EXT4 by mistake.  After nearly 40hrs of processing and 741G of data recovered I'm still left with a mess of 175,000 files with no original names to sort out and a lot of missing data.  PDF, JPG, GIF, html, txt, type files had a great recovery rate.  OpenOffice anything, Evolution backup, and several other file types were a virtual 100% loss.

Down side to EaseUS Professional is that even though it will read several file system types used in linux like EXT3 it runs in a windows environment and tries to put the data back into a windows compatible partition.  I miss read the software and thought that it read Linux partitions and ran in Linux...my bad.

I've tried TestDisk with zero success, I've also ran PhotoRec however every image it has recovered came with a significant loss in picture quality.  I'm continuing to try different techniques since I've left the original drive in it's reformatted screwed up condition and I'm transferring what I can to another External 1.5T.  Any other suggestions from people who've been there done that and recovered would be great.
Perfect world goal: Re establish the original EXT3 partition and/or pull all readable data off the drive with original file names intact. 

As too the original poster, once you realize you've screwed up stop right there before more damage is done, pull the drive from the system and replace with a different one get the bad hard drive into an external case and access it in a READ only mode to stop any more damage.

---

### Post by conradin on 2010-04-04
Ok, recovering data from EXT3/4 systems is one of the easiest, where multiple recovery points for super-blocks and inodes are stored. I have no idea where the idea to overwrite the existing hard-drive with a new OS came from, that is considered poor practice with any operating system. Still, Data recovery may be possible. What we need to know is a little about your partitions prior to what ever corruption occurred. If you do not know, perhaps you have information about the current File-systems / partitions. 

If you had a data partition, and a boot partition, and only over wrote the boot partition, recovering you data should be fairly simple. Was this the case?
to view your current partition setup:
```

sudo fdisk -l /dev/sda


```

If the partition with the data was over written, data will be more difficult to recover, but may still be possible.

---

### Post by acreech on 2010-04-04
> WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000604c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488386583+  ee  GPT


This is what happened with my drive. I ran into an error with my operating system (karmic). I tried to fix it and then screwed up grub. I rebooted and grub did not load so the computer would not boot. Then I went in with the live cd and moved the valuable data to the 2nd internal hard drive (that is the one listed above, although it is no longer internal). I re-installed Karmic on the 1st hard drive, not realizing that I would format the 2nd internal hard drive. 

It was formatted ext3. Now it is formatted ext4. The program that brcre mentions pulled off the most information on it, but there are linux specific files that were not recovered. These are the evolution backup, files from Open Office and Notedit. 

I have tried Photorec and Testdisk with limited results. 


acreech

---

### Post by acreech on 2010-04-05
Bump

---

### Post by conradin on 2010-04-05
Ok, the fdisk listing I see is of only 1 disk. As to why a second disk was reformatted during an install, Im not sure, but it had to be specified at some point. What youre telling us is you have recovered most of your data? 
(sounds pretty great to me) Changing the file-system often corrupts data, but if youve got some back, thats awesome. If youve backed up your recovered info, you could try remaking the file-system with mkfs with the idea that you will be going to ext3 from ext4. Im thinking that you did not format the drive if the data is still intact. what it sounds like was the partition was deleted and a new filesystem was wrote. Any ways, what you will have to do is unmount the filesystem you want to change and then specify the changes you want to make. Another program you might consider is debugfs. Another person has other ideas about how to migrate back to ext3. Waht makes data recovery really hard is trying to cope with overwriten data. The more changes that are made may overwrite other important data. 

try debugfs first, see what info you can get from that, then you may try the method out lined here:
[http://duopetalflower.blogspot.com/2010/01/how-to-migrate-ext4-partitions-to-ext3.html#step8](http://duopetalflower.blogspot.com/2010/01/how-to-migrate-ext4-partitions-to-ext3.html#step8)

or 
remaking the filesystem with mkfs then try fixing the errors that may occur using fsck.

---

### Post by acreech on 2010-04-05
Thanks for the reply. I went back in and messed withthe settings of PhotoRec. I think that I have found out how to use it better and it is finding some of those files that I have not previously found. I would like my JPG and email backup the most. there is a couple specific spreadsheets that I would love to have, but I have found most of everything else. 

Overall I have recovered alot, yes. There is just a few specific things that I have not come across yet. 

I will post back after PhotoRec gets done and maybe try your other suggestions (depending on the outcome of PhotoRec)

Thanks

acreech

---

### Post by brcre on 2010-04-05
For anyone else reading through this discussion, here are some reference material that helped acreech and me.

---

### Post by ranjank on 2010-04-09
> **AlexFox said:**
> AFAIK, it's very difficult to recover data from an EXT3/4 partition. Also, because you've reinstalled, there is a good chance that you've over written the data already. You can try and give this app a bash, haven't tried it my self

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

Thank u buddy , about 50GB recovered , got all important files .

---

