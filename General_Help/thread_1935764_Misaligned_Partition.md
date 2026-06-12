---
title: "Misaligned Partition"
date: 2012-03-04
forum: General Help
---

### Post by blur xc on 2012-03-04
I have two brand new seagate 2tb drives.  I just installed them in the computer and after running fdisk -l I get the "partition 1 does not start on a sector boundary" message.  I check the disk utility and it tells me the partition is misaligned by 512bytes.  I've tried deleting and re-creating the partition, in both ntfs and ext3 and it hasn't fixed it.  

Now, I'm only using those devices for mass storage, so from what I read I just thought I could leave it be and just deal with performance hit.  I mean, I not doing mass read/write operations, just storing photos.  So, I tried copying all the data from my old, filling up, 1tb drive and after a few mins the computer locks up solid.  Not even REISUB wold reboot it.  And after doing a hard reset, the drive won't mount anymore.  I don't recall what the error message was off the top of my head since I didn't save it and I'm in no hurry to try to reproduce it.  That was while it was still an ntfs filesystem.  I just formatted it as an ext3 but haven't tried writing anything to the drive yet.  

I'd like to get the partition properly aligned before writing anything to it.

I think they are barracuda green drives.  Not 100% certain.  I bought them from Costco on their black Friday sale last year.  They started out as external usb3.0 drives, but since I don't have usb3.0 ports on my pc, I removed the drives from their housings and stuffed them inside my tower case.  

I did do a search on this issue, and a lot of he people with this issue were using their drives as their primary boot device, with multiple partitions using a variety of filesystems, so I was having a hard time filtering out the relevant information.  I mean, my situation is pretty simple in comparison.  Just one big storage partition.

thanks,
BM

---

### Post by blur xc on 2012-03-05
I think the solution might be related to this post- [http://ubuntuforums.org/showpost.php?p=11375535&postcount=17](http://ubuntuforums.org/showpost.php?p=11375535&postcount=17)

If so, could someone dumb it down a bit?

thanks,
BM

---

### Post by blur xc on 2012-03-06
bump

Still playing around, but still haven't had any success...

BM

---

### Post by cryptotheslow on 2012-03-06
I believe the trick is to leave 2MB free space before the start of the first partition.

[http://www.linux-mag.com/id/8397/](http://www.linux-mag.com/id/8397/)
[http://www.wwpi.com/index.php?option...Itemid=2701018]("http://www.wwpi.com/index.php?option=com_content&view=article&id=8840:ssd-storage-demands-proper-partition-alignment&catid=99:cover-story&Itemid=2701018")
[http://lifehacker.com/5837769/make-s...ve-performance]("http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance")

You can resize or move partitions to align them using GParted from a LiveCD / USB if necessary.

I'm no expert on this so do some reading first :grin:

---

### Post by blur xc on 2012-03-06
> **cryptotheslow said:**
> I believe the trick is to leave 2MB free space before the start of the first partition.

[http://www.linux-mag.com/id/8397/](http://www.linux-mag.com/id/8397/)
[http://www.wwpi.com/index.php?option...Itemid=2701018]("http://www.wwpi.com/index.php?option=com_content&view=article&id=8840:ssd-storage-demands-proper-partition-alignment&catid=99:cover-story&Itemid=2701018")
[http://lifehacker.com/5837769/make-s...ve-performance]("http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance")

You can resize or move partitions to align them using GParted from a LiveCD / USB if necessary.

I'm no expert on this so do some reading first :grin:

Thank you!  I'm going to try that as soon as possible...  What gets me is why a factory partitioned and formatted drive, new out of the box, ships like this.

BM

---

### Post by cryptotheslow on 2012-03-06
I've no idea why that would be the case. As far as I understand these problems started arising when hard disk manufacturers started adopting a 4KByte physical sector size as opposed to the long established 512byte size that went before.

Further confusing things was that to try to maintain compatibility with partitioning tools that could only understand 512byte sectors some manufacturers introduced something of a fudge called "Advanced Format" which used an interpretation layer in the drive firmware to present each 4KB sector as 8 512byte sectors - which in turn had the knock on effect that even partitioning tools that understood the 4KB sector concept were tricked into treating the drive as a 512byte sectored one.

Happily things have moved on somewhat and new drives do correctly report their 4KB sectors and most related tools understand and can use them.

e.g.
```
crypto@ubulaptop1204:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/**physical**): 512 bytes / **4096 bytes**
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

However, if you have a 2TB drive and are just creating one big partition I'd have thought you could just start the partition at sector zero and be done with it. Unless it has one of those annoying manufacturer's tools & documentation auto-mounting CD mimicking partitions stuffed on the start of it. I know my Tosh usb drive does.

What does "sudo fdisk -l" (lowercase L) have to say about the disk?

---

### Post by blur xc on 2012-03-06
sudo fdisk -l has this to say-

```
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00036f27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   83  Linux
Partition 1 does not start on physical sector boundary.

```

Right now I trying it with the suggestions I found in that post I mentioned earlier, turning of dos compatibility and setting "it" to sectors instead of cylinders, as well as your suggestions of leaving some free space before the partition.  

fingers crossed...

The only other lingering question is what filesystem to use.  It's mass storage for my raw photos.  Right now I do all my editing in Linux, but you never know what the future holds...  I dunno... I really tempted by btrfs but afraid at the same time...

thanks again.  Your explanation really cleared things up.
BM

---

### Post by blur xc on 2012-03-06
Yay!  Operations completed successfully and fdisk -l tells me this now:
```
sudo fdisk -l /dev/sdd

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00036f27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953508352   83  Linux

```

Thanks for the help.  Now do do the same for my 2nd 2tb drive.  Now the lingering question yet to be answered is if this solves the computer freezing up while copying all my data over to it (about 800gigs worth).  

fingers still crossed...

BM

---

### Post by cryptotheslow on 2012-03-06
I have to admit I'm confused now.

Your start and end sectors are the same at 1 and 243201 respectively but the number of blocks has increased. I'm glad I said "I'm no expert on this" in my first reply - because clearly some piece of information is missing from my understanding. :D

Personally on my external drives that I use solely with Linux I stick to ext4 with LUKS encryption, for stuff that needs to be cross platform like USB sticks FAT32 or NTFS - probably NTFS would be recommended if you have to deal with raw image files that could bust the upper filesize limit of FAT32.

I read a lot of good things about btrfs and it seems to be gaining mainstream adoption lately - I've not tried it so can't comment. I guess I like to live in the "tried and tested" safe zone for stuff that I absolutely need to work reliably even at the expense of performance.

Ahhh - the joys of having a choice. vive la difference. Just use what works for you :)

***edit -*** one further thought, maybe partitioning with a logical sector size of 4096 bytes is the way forward to match the physical sectors - after all committing a change to a 512 byte logical sector is going to involve reading and rewriting the whole 4096 physical sector anyway. Would be wasteful on a drive with lots of very small files but for something used solely to store raw image files - maybe not so much as it would only be the last sector of each file padded out. Just thinking aloud there and probably with flawed preconceptions - may be best just to ignore this edit as it may have traces of carlsberg in it.

---

### Post by blur xc on 2012-03-07
> **cryptotheslow said:**
> I have to admit I'm confused now.

Your start and end sectors are the same at 1 and 243201 respectively but the number of blocks has increased. I'm glad I said "I'm no expert on this" in my first reply - because clearly some piece of information is missing from my understanding. :D

Yeah, you might as well be speaking greek right now.  

But I went ahead and formatted it to ext3 and copied all 800 gigs worth of files over between last night and this morning.  I first tried to do it the easy way and just cp -r * for the whole drive but it still froze up about half way through.  I still had use of my mouse and other windows worked, so I tried force-quitting the terminal session but the cp operation was still running (?-not sure) and then the whole computer froze up.  Had to do a hard reset.  I noted where it left off and then copied the remaining folders over in manageable chunks.  

I did a file count using "find . -type f | wc -l" for each parent folder (several sub folders in each with the actual image files) and the count came up the same each time.  I then did du -s for each parent folder, and the disk usage came back higher on the new drive.  I'm assuming that the metadata takes up more space on the ext3 filesystem?

Anyway- now to learn about rsync to keep the my data backed up onto the 2nd 2tb drive.  I've been playing Russian roulette up until now.  This will be my first time having actual backups. :)

Thanks again for the help.

BM

---

### Post by growingneeds on 2012-04-23
The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for newer installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignment issue.

Hope this helps.

---

