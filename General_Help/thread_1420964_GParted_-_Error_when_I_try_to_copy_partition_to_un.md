---
title: "GParted - Error when I try to copy partition to unallocated space."
date: 2010-03-03
forum: General Help
---

### Post by cmommsen on 2010-03-03
I'm stuck with just one extended partition on my HD, containing my OS in a logical partition, all the way to the 'right' in GParted. (The rest is all unallocated)  So I did some research and in order expand and make use of the rest (and larger half) of my HD, I need to copy the partition containing my OS into the unallocated space, make sure that I can boot it up and run it succesfully, and then delete the original and expand the new one to the right. (In GParted)  

Here's my problem:

Everything goes smoothly until about 3/4 way through the copy operartion, it quits, says there was an error reading a certain block (95159557), and I'm left with the partially copied partition which won't boot because there's "no device."

Please anyone who can help me out, let me know what additional data you need to know...

Thanks!

======================================================
GParted 0.4.5
 Libparted 1.8.8.1.159-1e0e
    **Copy /dev/sda6 to /dev/sda (start at 0.00 B)**  00:25:41    ( ERROR )             calibrate /dev/sda6  00:00:01    ( SUCCESS )             [I]path: /dev/sda6
start: 66428901
end: 112149764
size: 45720864 (21.80 GiB)[/I]          check file system on /dev/sda6 for errors and (if possible) fix them  00:00:16    ( SUCCESS )             ***e2fsck -f -y -v /dev/sda6***             [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  222660 inodes used (15.56%)
     400 non-contiguous files (0.2%)
     139 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 193013/61
 2493186 blocks used (43.62%)
       0 bad blocks
       1 large file

  159599 regular files
   25471 directories
      68 character device files
      26 block device files
       0 fifos
     402 links
   37482 symbolic links (29477 fast symbolic links)
       5 sockets
--------
  223053 files
[/I]       [I]e2fsck 1.41.9 (22-Aug-2009)
[/I]             create empty partition  00:00:04    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 45720989
size: 45720927 (21.80 GiB)[/I]          set partition type on /dev/sda1  00:00:01    ( SUCCESS )             *new partition type: ext4*          copy file system of /dev/sda6 to /dev/sda1  00:25:19    ( ERROR )             using internal algorithm       copy 45720864 sectors       finding optimal blocksize             copy 65536 sectors using a blocksize of 64 sectors  00:00:13    ( SUCCESS )             *65536 of 65536 copied*       *12.1521 seconds*          copy 65536 sectors using a blocksize of 128 sectors  00:00:13    ( SUCCESS )             *65536 of 65536 copied*       *13.0805 seconds*          copy 65536 sectors using a blocksize of 256 sectors  00:00:09    ( SUCCESS )             *65536 of 65536 copied*       *9.12832 seconds*          copy 65536 sectors using a blocksize of 512 sectors  00:00:09    ( SUCCESS )             *65536 of 65536 copied*       *8.75997 seconds*          copy 65536 sectors using a blocksize of 1024 sectors  00:00:06    ( SUCCESS )             *65536 of 65536 copied*       *6.16763 seconds*          copy 65536 sectors using a blocksize of 2048 sectors  00:00:04    ( SUCCESS )             *65536 of 65536 copied*       *4.69806 seconds*          copy 65536 sectors using a blocksize of 4096 sectors  00:00:05    ( SUCCESS )             *65536 of 65536 copied*       *4.14186 seconds*          copy 65536 sectors using a blocksize of 8192 sectors  00:00:03    ( SUCCESS )             *65536 of 65536 copied*       *3.82242 seconds*          copy 65536 sectors using a blocksize of 16384 sectors  00:00:04    ( SUCCESS )             *65536 of 65536 copied*       *3.50779 seconds*          copy 65536 sectors using a blocksize of 32768 sectors  00:00:04    ( SUCCESS )             *65536 of 65536 copied*       *3.78579 seconds*          copy 65536 sectors using a blocksize of 65536 sectors  00:00:04    ( SUCCESS )             *65536 of 65536 copied*       *4.07176 seconds*          optimal blocksize is 16384 sectors (8.00 MiB)          copy 44999968 sectors using a blocksize of 16384 sectors  00:24:05    ( ERROR )             *28009760 of 44999968 copied*       *Error while reading block at sector 95159557*          28730656 sectors copied          libparted messages    ( INFO )             *Input/output error during read on /dev/sda*          ========================================

---

### Post by quixote on 2010-03-05
This: [COLOR="Blue"]Copy /dev/sda6 to /dev/sda[/COLOR] looks wrong to me. It should go partition (sda6) to partition (eg sda1), not partition to whole physical drive (sda).  I'm pretty sure you first need to turn all that unallocated space into a partition, ie say "new", and format it to ext3 or ext4, whichever one you're using.  

I'm not sure whether you want to set it bootable or not.  I would.  And unset the boot flag on your current bootable partition.  Make the new partition and let that operation complete before the next step.

Once you have two partitions, then copy 6 to 1 or whatever the number turns out to be.  Try booting.  If everything works, you can keep the original partition separate, or add it to the one to the left.  As you've probably already noticed, it's easy to append space from the right to the left, but not vice versa.

By the way, are you running karmic? jaunty?

---

### Post by dcstar on 2010-03-05
> **cmommsen said:**
> I'm stuck with just one extended partition on my HD, containing my OS in a logical partition, all the way to the 'right' in GParted. (The rest is all unallocated)  So I did some research and in order expand and make use of the rest (and larger half) of my HD, I need to copy the partition containing my OS into the unallocated space, make sure that I can boot it up and run it succesfully, and then delete the original and expand the new one to the right. (In GParted)  

Here's my problem:

Everything goes smoothly until about 3/4 way through the copy operartion, it quits, says there was an error reading a certain block (95159557), and I'm left with the partially copied partition which won't boot because there's "no device."
........

Firstly, you better be off copying an **unmounted** partition, if you using a running system to copy that same system then you may have big problems.

Secondly, a bad block is a bad block, you need to do a full SMART test on the drive to (hopefully) remap the bad block.

Thirdly, there is no reason why you cannot expand any partition into free space, boot off a live CD and use the Partition Manager to do it.

---

### Post by cmommsen on 2010-03-05
> I'm pretty sure you first need to turn all that unallocated space into a partition, ie say "new", and format it to ext3 or ext4, whichever one you're using.

Ok, I'll try this and see what happens.  Btw, I'm running karmic and I ALWAYS use a live CD to do any GParted activities.  

Question:  If I unset the boot flag on my current partition, will I still be able to boot from it, in case the new one doesn't work?

Oh and what's a SMART test, and how do I get/run it?

---

### Post by louieb on 2010-03-05
I've had Gparted fail when copying a partition before. 
Got around it by using partimage to do a backup from the old  and restore to the new. (does not work if the partition uses the ext4 file system)
 
Might trt FSArchiver if the partition uses ext4.

---

### Post by cmommsen on 2010-03-05
Ok now I'm in a slightly deeper water... I tried creating a empty partition and copying the one containing my OS into it.  Gparted wouldn't even let me paste... so I tried deleting the Extended partition which was around the one containing my OS.  And it seems that when you do that, all the partitions inside get deleted too. 

So now I'm on the LiveCD, running testdisk to try and recover the partition table.  However, testdisk says that the partition I want is "unrecoverable"

[IMG]http://https://mail.google.com/mail/?ui=2&ik=80828f7511&view=att&th=1272fbe16e36f2c6&attid=0.3&disp=inline&realattid=f_g6fd2uv82&zw[/IMG]

[IMG]https://mail.google.com/mail/?ui=2&ik=80828f7511&view=att&th=1272fbe16e36f2c6&attid=0.1&disp=inline&realattid=f_g6fd20ge0&zw[/IMG]

---

### Post by quixote on 2010-03-05
Ouch.  First, like it says in the Hitchhiker's Guide to the Galaxy: [COLOR="Blue"]Don't panic![/COLOR]  So long as it's not overwritten, all the actual data and OS on your disk are still there.  So don't do any more disk accesses than you need to.  

If you have well and truly erased the partition table, the only alternative is direct disk reads.  (More on that in a sec.)  I don't know if there are better things than testdisk for examining erased partition tables.  There might be.  So the first thing is to search for that.  Something along the lines of "ubuntu recover erased partition".  (Don't include the quotes, but do include all the search terms.)

If you can recover the partition table, then that's good....  Then we can go back to trying to get gparted to do what you want.

If recovering looks like a lost cause, then if you have your important data backed up, the best thing to do is reinstall.  The bright side there is you can format the disk to the right number and size of partitions from the start.

If it's not backed up, then what I would try is to do is the following. (Caveat: I've never had to do this, so I'm just saying what I would try.) 

Try photorec following the detailed instructions here: [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/).  As you can see from the instructions, recovering several GB of files that way is going to be seriously tedious.  That's why I recommend reinstalling if you possibly can (unless it turns out you can recover the partition table).  If you have just some critical files, you could concentrate on trying to recover those.

Meanwhile...try not to get too frustrated!  Put it down to a learning experience.  Just think how many people with similar problems you'll be able to help after you fight your way through this one! 8-[

---

### Post by cmommsen on 2010-03-05
It's not so much that there's any VALUABLE data... just a few hw assignments that I'd have to start over again. :( But the biggest reason I'd like to get my OS back without reinstalling is I really LIKED my OS... And it took me a long time to get everything like wireless, ALSA, and the graphics drivers all in working condition. I guess I should have kept better records while I was doing all that....
 
But what were you saying about 
 
>  
the only alternative is direct disk reads. (More on that in a sec.) 

 
How do I do a direct disk read... Or what would happen if I went ahead and used testdisk to recover the extended partion? (Right now it says it's deleted and I can't read any of the files when I hit 'P' because they're "corrupted".  But I could still select the partition as "primary boot" and hit 'continue'...

---

### Post by quixote on 2010-03-05
Sorry, I wasn't clear.  photorec is a method of doing direct disk reads.  It's something you can get at via testdisk, as I understand the instructions.  Since you'll be working from a liveCD, any installs you do are just for the session, so you'll need to go through the rigamarole of getting testdisk again.  Follow the instructions at the link.  psychocats gives A+ instructions.

I'm not sure what happens in testdisk when you select "primary boot" and "continue".  Are you sure you're not telling it to *create* a primary boot partition?  You don't want to do that yet.  You want to recover off of there, not write to it.

I forgot to mention re keeping better records as you do umpteen customizations: I've been promising myself that next time I'm going to do that for about 5? 10? years now.  :D

---

### Post by cmommsen on 2010-03-06
Haha well that's not very encouraging for me... ;)

Here's what I meant.  After you do a deep scan with testdisk, it first says "the following partions cannot be recovered" :(  and displays those partitions and their starting and ending blocks, and size.  So from that info, I'm pretty sure the one I want is among them.

Next, after you hit continue, testdisk displays all the rest of the partitions it found, all as "deleted" (they're white, not green).  However, I can use the arrow keys to change them to either primary, logical, or primary boot.  Then I  *could* hit continue, and it would proceed to undelete those that I changed.  I will re-do the scan and paste the results here momentarily...

---

### Post by cmommsen on 2010-03-06
Ok here's what I got:  
From quick scan.  The first message after it completes...

> TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63

The harddisk (60 GB / 55 GiB) seems too small! (< 68 GB / 63 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                 5469   0  1  8314 252 63   45720864

I will now perform a deep scan...









[ Continue ]
EXT4 Large file Sparse superblock Recover, 23 GB / 21 GiBThen,

> 
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  4134 254 63   66428712
P FAT32 LBA             6903   0  1  7294 254 63    6297480 [DellRestore]










Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 34 GB / 31 GiB

Result of Deep Scan:
> 
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63

The harddisk (60 GB / 55 GiB) seems too small! (< 86 GB / 80 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                 3415   0  1 10524 253 56  114222080
  Linux                 3417   2  1 10527   0 56  114222080
  Linux                 5469   0  1  8314 252 63   45720864








[ Continue ]
EXT4 Large file Sparse superblock Recover, 58 GB / 54 GiB

and then,
> 
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1  4134 254 63   66428712
D HPFS - NTFS              6   0  1  6902 254 63  110800305
D Linux                 4135   2  1  6980 254 63   45720864
D FAT32 LBA             6903   0  1  7294 254 63    6297480 [DellRestore]
D Linux Swap            6981   1  1  7109 254 63    2072322
D Linux Swap            7110   1  1  7295 254 63    2988027






Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 34 GB / 31 GiB

---

### Post by quixote on 2010-03-07
Just saw your message.  Have to get to sleep, unfortunately.  I'll be back tomorrow, when I've un-pie-eyed myself and can try to understand the output.  I've never done that option in testdisk, so I want to be sure I don't steer you wrong.

---

### Post by quixote on 2010-03-07
Well, I've stared at the output, and I don't get it.  How can it see the partitions and yet insist it can't recover them?  Makes no sense.  There has got to be something out there that can scan the sectors on the disk and rebuild a partition table if it can see the partitions.  Maybe testdisk will do that, but I'm just not understanding the options.  What we need here is somebody who knows more about this than I do. 

(About an hour later...)  I tried to make one more attempt at figuring this out, and damned if there isn't a [wikipedia page]("http://en.wikipedia.org/wiki/TestDisk") I've never noticed before.  That has a number of interesting links, but the one I followed was to a [debian help page]("http://www.debian-administration.org/articles/420") with a good bit of info.  I'm still not clear after reading it whether testdisk will or will not recover lost partitions -- sounds like it will, but I'm still not sure exactly what steps you're supposed to follow. It doesn't seem to say what to do if it *has* found the partition, as in your case, but *also* says it's unrecoverable.  Very frustrating. Maybe if you read it more closely than I did, something will click?

---

### Post by cmommsen on 2010-03-08
Nope, nothing clicked. Well I ended up re-installing and this time around I found a really cool tool for building a Dell-based ISO image that has all the drivers for my Dell laptop included.
 
[http://ubuntuforums.org/showthread.php?t=1141757](http://ubuntuforums.org/showthread.php?t=1141757)
 
It even builds a back-up partition on my HD! So in the end, I'm actually glad this happened. My system works 10x better than before.... 
 
...still would like to know what's up with test-disk not being able to rebuild SOME deleted partitions...
 
...and what's up with GParted not being able to PASTE the contents of one partions into another of the same format.... 
 
....oh well I guess I'll mark this as solved. Thanks for trying! :)

---

### Post by quixote on 2010-03-15
I'm glad things are working, but it's too bad none, as in zero!, of your questions got answered :(.  Not sure "solved" is the right word . . . :?

The link looks like it might be useful for info on how to make custom bootable media in general.  Something I've been trying to figure out for ages.  (Remastersys has never worked for me.)

---

