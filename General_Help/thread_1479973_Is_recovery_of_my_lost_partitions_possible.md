---
title: "Is recovery of my lost partitions possible?"
date: 2010-05-11
forum: General Help
---

### Post by vanRaewa on 2010-05-11
Yesterday, I decided to install Debian (Lenny) side by side with Ubuntu 10.4 and Windows 7. I
went ahead and reserved about 30 GB of space by shrinking an NTFS-volume (had about 90 GB free space)
with Windows 7:s disk manager. This space was located between the NTFS-volume (at the beginning) and
my Ubuntu /-partition (about 15-20 GB). The Ubuntu /-partition was followed by my /home-partition 
(about 60-80 GB) and lastly 3.96 GB of swap space. The NTFS-volume, /- and /home-partition as well
as the swap disk where primary partitions (no particular reason, however I didn't plan to install 
any other OS at the time). 

/dev/sdb [ [NTFS ~370GB] [ ~30 GB unallocated ] [ / ext4 Ubuntu ~15-20GB ] [ /home ext4 ~60-80GB ] [SWAP 3.96GB] ] <-- 500GB total

I installed Debian on an ext3-partition of about 15GB - my plan was to share the /home-partition with Ubuntu, but 
as I installed Debian I found out that it doesn't support ext4 so sharing the /home-partition was out of the question.
Since I didn't check how many primary partitions the disk had, and I thought there where only three, the /-partition of
Debian was also made into a primary partition

/dev/sdb [ [NTFS ~370GB] [ ~15 GB unallocated ] [ / ext3 Debian ~15GB ] [ / ext4 Ubuntu ~15-20GB ] [ /home ext4 ~60-80GB ] [SWAP 3.96GB] ]

Later, in Windows 7, I decided to just delete the Debian partition since the /home-deal didn't work. I saw an odd thing in the disks'
partition map - the /- and /home-partitions of Ubuntu where contained within logical partition. It seemed a little odd, but I thought
it could well be the case that I partitioned it this way and forgot about it (or something).

[ [NTFS ~370GB] [ ~15 GB unallocated ] [ / ext3 Debian ~15GB ] <[Logical [ / ext4 Ubuntu ~15-20GB ] [ /home ext4 ~60-80GB ] ]> [SWAP 3.96GB] ]

So the /-partition of Debian was deleted - and to my horror I saw this:

[ [NTFS ~370GB] [ ~30 GB unallocated ] <[Logical UNALLOCATED ~100GB ]> [SWAP 3.96GB] ]

Scared to death, the only thing I thought of was to shutdown the computer (some vague hope of "undoing" this horror"). On those two partitions
where a lot of school work (including a virtual machine with my B.Comp.Sc. Thesis Project.....), photos, music and the like. I immediately went 
to buy a 1TB disk to store an image of the whole drive (using dd), and then I installed Ubuntu on the disk, and during most of the night dd 
completed the image. BTW, when I booted into Windows its Disk Manager detected Linux-partitions on the new disk as located within a logical partition,
even though there where only two primary partitions on the disk (wtf???). Seems a bit.... unsafe...

I then let TestDisk do a deep search on the old disk, and it could find a lot of Linux-partitions including the Debian one, but it didn't seem like 
it could restore them (maybe I missed something...). I am completely lost now, and in serious need of some help :(

Is there any chance to restore this partition at all?

---

### Post by dandnsmith on 2010-05-11
I think you're talking about having *logical* partitions within an *extended* partition - which is the way you get more than 4 partitions on a HDD (a limitation of the original partition table design)

If you have a good enough record of sizes or start/finish of the deleted partitions, it is possible to recreate the partition table entries - but it needs care. I seem to remember someone talking about partition recovery, but not what the tool was. I always keep a record of what fdisk shows, just in case, and it has stood me in good stead more than once. I use fdisk for manipulating partitions - probably because I got used to it when there was no graphics interface and suitable tools (also, gparted just doen't give the same info).
It's quite possible that the results testdisk came up with have the necessary data to redefine the partitions.

Even when created anew you may still have a bit of a problem with the partitions, as they will have different blockids (I think), so Ubuntu's method of referencing will break down - this, too, can be overcome.

---

### Post by sbergman on 2010-05-11
Hi,

Ok maybe I can help with recovering some of your data, but unfortunately not with the partition..... I'm not familiar with testdisk, but have done some data recovery with software called 'foremost' recently, which I presume would do the same thing as testdisk. 

There's also a liveCD linux distro at [http://www.deftlinux.net/](http://www.deftlinux.net/) which contains some nice data recovery stuff.

---

### Post by vanRaewa on 2010-05-11
> **dandnsmith said:**
> I think you're talking about having *logical* partitions within an *extended* partition - which is the way you get more than 4 partitions on a HDD (a limitation of the original partition table design)


Yes, that would be it. I'm a bit fuzzy on the terminology since it was a while ago it was needed :)

The weird thing is that there wheren't initially an extended partition  - only 4 primary partitions. I guess that when I made the 5th primary partition (Debian), the debian installers' partition manager encapsulated the / and /home partitions (Ubuntu) within an extended partition and converted them to logical ones instead (or something like that). 

The partition manager didn't warn me or anything, so I don'&#7831; really know what happened. All I know, or at least fairly certain about, is that there where no extended partition before.

---

### Post by vanRaewa on 2010-05-11
> **sbergman said:**
> Hi,

Ok maybe I can help with recovering some of your data, but unfortunately not with the partition..... I'm not familiar with testdisk, but have done some data recovery with software called 'foremost' recently, which I presume would do the same thing as testdisk. 

There's also a liveCD linux distro at [http://www.deftlinux.net/](http://www.deftlinux.net/) which contains some nice data recovery stuff.

Sounds interesting - I'll try foremost right away :)

By the way, I found a backup of my home folder hidden in one of my other disks that I made prior to making a clean install of Lucid Lynx. The loss
of data is now almost bearable :)
But I still want to try to restore the data if possible...

---

### Post by vanRaewa on 2010-05-11
I don't really want this to happen again, but I don't have enough space to backup my HDDs with whole images. Isn't it possible to just take a backup of the partition tables, given that I don't resize partitions that often?

I mean, the data is all there unless overwritten, so shouldn't it be enough to just save the "pointers" to all the files instead of making a disk image of the whole HDD? Wouldn't that save me from these kinds of accidents (not counting HDD failures, failed move/resize of partitions etc)?

---

### Post by srs5694 on 2010-05-11
> **vanRaewa said:**
> I don't really want this to happen again, but I don't have enough space to backup my HDDs with whole images. Isn't it possible to just take a backup of the partition tables, given that I don't resize partitions that often?

Yes. See the "Final Conversion Thoughts" section of [this Web page of mine.](http://www.rodsbooks.com/gdisk/mbr2gpt.html) It describes how to make both dd and sfdisk backups of MBR partition tables.

Of course, you're well advised to back up your entire hard disk, or at least your important user data. A partition table backup can help you recover from certain types of disk accidents, but it will be useless against some other problems (a disk that dies completely, an accident with dd that wipes out a whole partition's contents, etc.).

---

### Post by dandnsmith on 2010-05-11
I cannot get to the page you linked - is there a known problem?

Basically, I was interested as to what you'd say about backing up the details for the logical partitions depending from an extended partition, as these aren't held in the initial partition table.

Note to OP:
There can be only 4 primary partitions in a standard HDD partition table, and any extended partition counts as a primary for these purposes. This is why, when you ask for 5 partitions, the 4th primary will be converted to an extended partition reference, and that partition and any additional added within its envelope.

---

### Post by srs5694 on 2010-05-11
> **dandnsmith said:**
> I cannot get to the page you linked - is there a known problem?

Sorry; I accidentally pasted in a URL that's valid on my LAN but not on the Internet. I've fixed it. The correct URL is [http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html).

> Basically, I was interested as to what you'd say about backing up the details for the logical partitions depending from an extended partition, as these aren't held in the initial partition table.

That's why sfdisk is useful for this task -- it can create a text file that contains information on all the partitions, and you can feed that file back into sfdisk to recreate the partitions. This file lacks the MBR's boot loader data, but it can recreate primary, extended, and logical partitions.

---

### Post by vanRaewa on 2010-05-12
Thanks for the tip, this will be useful :) 

I don't use dd that much and I've never had an HDD die on me (it's an unlikely risk I'm willing to take since). I think backing up the partition table will suffice (for now), but I've been thinking about mirroring one of my 500GB HDD onto my other one and keep all important information on those.

---

### Post by dandnsmith on 2010-05-13
srs..
thanks for the corrected link.
So useful that I already passed on to another posting - and it seems to explain (possibly) quite a few of the problems that people are having with new PCs, wanting to install Ubuntu etc after Win7. I can recall at least one more where the install just wasn't showing existing partition info.

---

### Post by srs5694 on 2010-05-13
The page to which I linked is part of the documentation for my GPT fdisk package, and the bulk of that page is about conversions between partition table formats. The last section was relevant to the question because it deals with partition table backups. The problems of the Ubuntu partitioner failing to "see" all the partitions are unlikely to be related to different partition table formats, since the Ubuntu installer understands both MBR and GPT (the two most common partition table formats). The ones I've seen in enough detail seem to be mostly related to issues of a damaged MBR partition table. Most commonly, the extended partition is bigger than is legal for the disk and needs to be resized. I've also seen at least one post from somebody who had problems because Ubuntu lacked drivers for the SATA chipset used on the computer.

---

### Post by dandnsmith on 2010-05-14
Thanks for that additional data.
I understand your qualification of my comment - and what you add reinforces my impressions.
I'd like to have come across such damaged examples myself, just to see the detail.
The bit about the lack of relevant SATA drivers is also something for me to try to remember - I'm still trying to learn, but suffering from aging memory problems.

---

### Post by obscurant1st on 2010-05-14
once somehow my partition table got currupted. and all my partitions were gone. I used testdisk to get back all my data. just restored the partition table using testdisk. one drive had one problem. for that particular partition the last cylinder was out of the original range.
So i had to manually delete that partition and create the partition according to the correct number of cylinders.

---

### Post by srs5694 on 2010-05-14
> **dandnsmith said:**
> I'd like to have come across such damaged examples myself, just to see the detail.

FWIW, I've seen enough posts about this that I decided to put up a Web page on the topic:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

It's easy enough to recreate the problem with a hex editor if you know what you're doing. (Tip: If you need to ask how, you don't know what you're doing! ;) ) I've seen enough posts from people with this problem to suspect that there's a moderately common utility out there that's creating damaged partition tables, but I'm not sure what the utility is.

---

