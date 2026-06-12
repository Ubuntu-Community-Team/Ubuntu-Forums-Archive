---
title: "Partitioning"
date: 2011-07-09
forum: General Help
---

### Post by Howy on 2011-07-09
So, recently, I had my partition table repaired, but now I want to change something, and wonder if it's safe...
I have a BIG extended partition. It's at about 750Gb. Aside from that, I have 2 unallocated spaces, one at 240Gb and one at 5Gb. I want to make one of my storage drives bigger, and so that I can take advantage of all the space I have. (Those 250Gb have been unused for ages. I want to use them for my growing libraries.)
So I wonder: would it be safe to put these smaller "chunks" into the extended partition, and still have a working systen? I don't want to mess it all up.
Also, can I safely resize a partition, like adding the extra space, without touching the existing data? I'm not exactly sure how the resize/move function in GParted works. Will it wipe and extend or only extend it by adding it?
It would be nice to have these questions answered. :)

Also, if it's to any help, this is my partition table as of now:
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=493631487, size=1450127361, Id= f
/dev/sda5 : start=493631488, size=463468544, Id=83, bootable
/dev/sda6 : start=957102080, size= 19650560, Id=82
/dev/sda7 : start=976762880, size=966995968, Id=83
```As for the first entries, they're unallocated. They're the primary drives, but they don't exist.
I'm actually considering to move my partitions out of the extended one, because I only have 3 partitions that I use and will ever use.
But if the extended partition is not a problem, I will just keep it this way.

I'd imagine that I first extend the extended partition to consume the unallocated space, and then I move it all to the end of the partition, and then resize sda7 to consume it, and get a 750Gb partition. :) 
Can this be done without loss of data?

---

### Post by pqwoerituytrueiwoq on 2011-07-09
when moving/resizing partitions there is always a risk of a big F up and moving is SLOW it is faster to shrink it 1st then move
you could mount the partitions in the current file system with fstab much quicker
sample line
```
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /home/me/.VirtualBox/HardDisks  ext4    defaults                             0       2
```you could mount it in /mnt and symlink to it

---

### Post by HermanAB on 2011-07-09
Playing with the partition table is never safe.

---

### Post by Howy on 2011-07-09
Ok... I think I'll make a separate partition for that unallocated space and symlink it instead of taking any risks.

---

### Post by ajgreeny on 2011-07-09
To make things a lot clearer, can you run gparted, and take a screenshot and attach it to this post.  It will be a lot easier to suggest a plan of action if it is possible to see the current partitions and their usage.

I am also a bit baffled by your comment:  "As for the first entries, they're unallocated. They're the primary drives, but they don't exist.", and I would like to understand that a bit better.

---

### Post by Howy on 2011-07-09
Ok, here's the graphical representation of my partition table:
[IMG]http://dl.dropbox.com/u/9280885/GParted.png[/IMG]
You obviously see the unallocated space at the beginning and the end of the disk. I'll have to wipe those once because GParted messed up a bit, but it's not much.
Mainly, I'd like to put all the unallocated space into the extended partition, and join it with sda7.
The time it takes doesn't really matter. In fact, I've done something similar before, and it didn't take too long. In addition, I'll have back my older computer today, so I'll be busy with that for a while. (I'm a bit nostalgic when it comes to WinXP...)
Also... The text is in Norwegian... But I hope it's still understandable?

---

### Post by pqwoerituytrueiwoq on 2011-07-09
boot live cd/usb
unmount swap
grow swap
grow extended
grow sda7
create ext4 partition at beginning of drive

edit fstab and have it mount the new patition as i stated before
i am guessing windows used to be at the beginning of the drive and you ditched it

---

### Post by Howy on 2011-07-09
Uh... I had Windows on another HDD. The unallocated space you see is from a previous backup partition, which didn't do it's job. It was swapped for an external one.
So, now I just want to get more storage. And, at the moment, my whole system is backed up. If the internal drive was wiped, I wouldn't care a lot, but I'd rather avoid it.

---

### Post by srs5694 on 2011-07-09
Something along the lines of what pqwoerituytrueiwoq suggests seems sensible. I'd suggest a few changes, though:


[list]
[*]Back up your partition table before you do anything else. You can do this with sfdisk, as in "sudo sfdisk -d /dev/sda > parts.txt". Store the parts.txt file on a removable disk (USB flash drive, CD-R, floppy, etc.) so that you'll be able to restore it should things go badly wrong.
[*]IMHO, there's no point in growing the swap space. The gap at that point is only 5 MiB (that's MiB, not GiB) in size, and so is trivial. There's no point in risking a crash, power failure at exactly the wrong moment, etc., that might end up trashing the partition table just to get an extra 5 MiB in the swap space.
[*]I'd mount the new partition to a mount point in /media/Lagring directly, rather than mount it at /mnt and create a symlink. That's a bit more direct. OTOH, this assumes that /media/Lagring is specified in /etc/fstab. If it's not, I'd set it up to be mounted via /etc/fstab, along with the new partition.
[/list]


In the long run, either completely redoing the partition table or switching to an LVM configuration would help consolidate disk space so that you've got one big user data filesystem (presumably mounted at /home) rather than three (enough is used in / that some user files are almost certainly stored there; plus /media/Lagring; plus the new partition). Such a reworking of the partition table right at this moment probably isn't worthwhile, though, unless you think it will be awkward to have your user files scattered across three partitions in the near term. If so, you can either transition to an LVM setup by stages or do some massive move or copy operations. Either way will involve a significant learning curve but can be done with minimal risk to your data if it's planned carefully.

---

### Post by Howy on 2011-07-09
Well, I want to extend the sda7 partition to avoid stuff scattered on 3 partitions. I think it works fine as it is, where I have the sda7 for media, like VirtualBox and pictures and videos.
If I get the sda7 to consume those 240Gb, it will be the only change I'll do for months, or maybe years.
I'm sure that I won't change it anytime for something like trying out an OS, because I have VirtualBox. But for VirtualBox, I want more space. And I can get that by extending sda7.
And as for mounting, I have set up all the partitions I need, the storage/sda7, the swap and root. That's how I want it to be. And I don't need to move the /home folder, as I move stuff over to the storage as needed.
But I'm still unsure about what you're suggesting: would it be a good idea to expand the sda7 by doing as I suggested? If the process of moving and resizing is successful, there won't be any loss of data, I assume?
This will be a long-term solution. I can tell you that.

---

### Post by ajgreeny on 2011-07-09
It is not a simple job to add the free space at the start of the disk to sda7, mainly because they are not next to each other, and it would involve moving everything in sda5 backwards to the start of the drive, a very longwinded and potentially dangerous activity, though I have to admit I have done it myself, but on a much smaller partition than yours.

For safety's sake I think it would be much easier at the moment to simply enlarge the extended partition sda4 back into the free space at the beginning of the drive and also to the end of the drive.  You can then enlarge sda7 to the end of that extended partition, and finally make a new ext2/3/4 partition to use as storage, mounted at boot with a line in /etc/fstab, at the beginning of the drive.

If you should decide to risk a complete overhaul of your partitions, I suggest you use clonezilla to clone each one separately, which will of course act as your backups of everything as well.  Then use gparted on a live CD/USB to edit/move/enlarge your current partitions, but be prepared for it to take many hours.

All may work out OK for you, but if not, you will at least have your clones, so will be able to make new partitions as you wish, but make sure each new partition is at least as large as the current layout, as your clones can not be restored to smaller partitions than they came from.

I hope that all makes sense to you.  Perhaps the simplest thing is just to leave current partitions as they are at the moment, make a new one in the free space at the start of the disk for storage, but then, when a new version of ubuntu arrives and you want to upgrade to it, do a clean install into a completely new partition layout, having first backed up all your data and /home.

---

### Post by westie457 on 2011-07-09
hello i did something similar to this a few days ago. Feel free to follow the route and adapt to suit your circumstances. 


[http://ubuntuforums.org/showthread.php?t=1798827](http://ubuntuforums.org/showthread.php?t=1798827)

The very first part does not apply in this case. The rest is relevant


                         =====================================================

Just remembered something. Using Gparted to copy and paste a partition to a different part of the hard drive they are changed to Primary partitions with possible problems with Grub as the UUID is changed I think. I found that very early when I tried to copy and paste Swap. It will be better to resize the extended and move the contents. I hope you like coffee, you are going to be drinking a lot as all this takes a long time.

---

### Post by Howy on 2011-07-09
I think I'll be able to cope with some hours of wait. Tomorrow, I'll be playing with my old WinXP. (A lot to clean up and set up, and I can play games while I wait. I also have a N900, so...)
And in addition, I have fully backed up my system. (I only have to go a short round with Deja Dup, and that's it.)
So, yeah: I choose to resize the sda7. And I am confident that nothing can or will go wrong. (Because I have backups.)
I'll boot it up tomorrow on a liveCD, and set it up to repartition. And if it does go wrong, I will simply restore the back up. (I love my 2Tb external. :) )

As for the time it takes, I have belief in the quad-core running at 3Ghz and the 6Gb of RAM to do it in a reasonable amount of time.

Ok, I'm ready to fire. I've set it all up to move, and I am confident that it will be as painless as when westie457 did it. (I'll be putting the space into the extended, then move around the contents and expand the sda7 to consume it.)
Sadly... I don't drink coffee just yet. I'll be chilling off infront of a 32" TV waiting for Windows to do what I tell it to. (Yeah, it's a 3,2Ghz and integrated graphics and 1Gb RAM... What can you expect? But it does play Halo 2.) I'll also be tweeting about how slow Windows Installer is, so yeah, I have lots to do... :p
And if this takes a lot of time, I'll just play Halo 2 all over again. (It's been over a year since I played it. Such a big moment... :') )

Firing in 3... 2... 1... Go!

Well, It will be as good as done in about 2 hours. 3 hours isn't that bad, really.

Okay... Only 1 hours left... xD And it's been going for 12 hours soon... How interesting...

Ok, it's finished,and ALL my data is... Still there! :P
Yeah, it all went as planned. I set up a BIG list in GParted, and everything was successful, There was no loss of files, and now my storage partition is larger than ever. (685Gb... That's enough for now. It's now half-full.)
Anyways, I thank you for all the support. I'm still unfamiliar with the forces behind partitions and how it works, but I've learned a good bit.
I hope I won't have to bother you all with my noobish questions for a while... :wink:

---

### Post by srs5694 on 2011-07-11
[Edit: I didn't notice the second page of responses, so this advice came in late. I'm leaving it in case somebody consults this thread in the future....]

To expand /dev/sda7 by more than the 4.66 GiB sliver of free space at the very end of the disk, you have a number of options, all with downsides:


[LIST]
[*]Create an LVM configuration, starting with a new partition in the free space at the start of the disk. Move as much from /dev/sda7 as you can into that free space, resize /dev/sda7 to its smallest possible extent, create a new partition to add to the LVM configuration in the resulting free space, move the rest of the /dev/sda7 data into the LVM, and convert the (now empty) /dev/sda7 to LVM form and add it to the logical volume in the LVM. This is tedious and presents a significant learning curve. If you're careful, though, it's relatively safe.
[*]Create a new partition in the free space at the start of the disk, copy /dev/sda5 into that space, reconfigure your boot loader to boot from that partition, delete /dev/sda5, move your swap partition to the start of the extended partition, and expand /dev/sda. This results in a somewhat "cleaner" final layout than does the previous option and there's no LVM learning curve to deal with; however, there's a risk that you'll lose your entire /dev/sda7 partition should there be a power failure, crash, or bug that pops up at the wrong moment.
[*]Much like the previous option, but instead of copying /dev/sda5, expand the extended partition and move /dev/sda5 to the left. This might be a bit easier, but there's the added risk of trashing /dev/sda5. You probably won't have to re-install your boot loader, but that's not certain, so you should be prepared with an emergency disc in case that should be necessary.
[*]Back up everything to another disk, completely repartition, and restore it all. The end result would likely be much like one of the previous two options. It'd be a bit more tedious, but possibly safer, depending on whether you've got adequate backups in the previous two methods.
[/LIST]


There are further variants and hybrids on all of these, but these are the major approaches that spring to my mind.

Personally, I wouldn't try any of these except possibly the first without having adequate backups or unless the data wasn't very important to me. Moving or resizing partitions, particularly when the operation involves the partition's start point, poses the risk of trashing the partition's data. Unfortunately, although the LVM option poses fewer risks, it's also the one that requires the most learning, and the resulting layout is ugly and inefficient -- the final substitute for /dev/sda7 will be scattered all over the disk. Furthermore, if the LVM option is appealing because of its reduced risk and therefore reduced need for backups, that exposes a problem: You *need* backups to protect against disks failing suddenly, human error, bugs, malware, etc.

---

### Post by Howy on 2011-07-12
That is a really good overview of how to repartition. Good work. It will probably be useful for many who are searching for ways of doing this. :)

---

### Post by pdlethbridge on 2011-07-14
yours looks like mine.  My goal is to have 3 flavors of ubuntu

---

### Post by pdlethbridge on 2011-07-16
I would love to be able to run at least 3 ubuntus and be able to remove and replace versions as I want but I can only add 1 next to an existing version
 Would fixing some thing in the boot loader of ubuntu on an install be possible

---

### Post by pdlethbridge on 2011-07-16
I would love to be able to run at least 3 ubuntus and be able to remove and replace versions as I want but I can only add 1 next to an existing version
Would fixing some thing in the boot loader of ubuntu on an install be possible

 I got this far    [http://ubuntuforums.org/attachment.php?attachmentid=197495&d=1310698621](http://ubuntuforums.org/attachment.php?attachmentid=197495&d=1310698621)

---

### Post by pdlethbridge on 2011-07-16
this is the latest view from gparted
looks Very much like yours in fact I used it to do mine

---

### Post by pdlethbridge on 2011-07-16
16, 17, and 18 are bad, only 19 is good
 sda 1,7 and 8 will be used for kubunt and other versions, I have room for more
As I have been thinking about it,  kubuntu and ubuntu are the same except for the gnom, kde difference,. therefore I can have 4 OS on 2 partitions and us the extra space for something different

---

### Post by Howy on 2011-07-19
Multiple Ubuntus, huh?
What happens when you try to install a third one?
I'm a bit confused by all the partition tables you've posted: which one is the present one?

I don't see why it won't work with three installations. It will share the swap automatically, and they will most likely not harm the other installations.
Have you used the regular installer, and installed it onto the desired partitions? That way, it shouldn't harm the other partitions at all, and keep them intact while installing as normal.

---

