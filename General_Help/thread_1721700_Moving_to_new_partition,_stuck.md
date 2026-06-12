---
title: "Moving to new partition, stuck"
date: 2011-04-04
forum: General Help
---

### Post by MMDeveloper on 2011-04-04
I have a laptop with a large harddrive. Originally I had the sda1 which was a dell recovery partition, sda2 which is my Win7 partition. I created a new primary partition to try out ubuntu. Falling in love with the OS, I wished to grow the partition but I already had 4 primary partitions.

I deleted my swap partition and converted that to an extended partition, I then grew it to a 100gb extended partition. I created 2 new primary partitions, one for swap and one for the OS.. So my drives are as follows:

sda1 - OEM System partition
sda2 - Windows 7
sda3 - NEW Extended partition
sda4 - old OS partition
sda5 - NEW Swap partition
sda6 - NEW OS Partition


This is what I have done thus far:
1. Booted to live CD
2. Mounted /dev/sda4 and /dev/sda6
3. cp -afvR /oldOSPartition /newOSPartition
4. In the NEW OS partition, I updated /etc/fstab to reflect the UUID's of the new disks.
5. I updated /etc/mtools.conf and /etc/mtab as well.
6. I rebooted to old OS partition and ran update-grub && update-grub2
7. I can see the new entries in the grub boot menu
8. I select the kernel entry for /dev/sda6 (NEW OS), it boots, but when I hit the desktop, I open an terminal and do a "mount" and I am somehow still mounted/booted to sda4 (old OS).

From here, I re-mounted /dev/sda6 to a temporary mount point and did a "cd /; grep -r 'sda4' * > /matches.txt"
I also searched for the UUID and I found no matches so I don't know why it reverted to sda4.

Even if I boot to the recovery console entry for /dev/sda6 in the grub menu, same thing, it keeps mounting sda4.

I've obviously missed a step somewhere. Help?! :(

---

### Post by Dutch70 on 2011-04-04
Hi and welcome to UF

Why don't you leave sda4 and use sda6 as a /home partition? Unless I'm missing something, that is by far the best way to go. 

You may even want to shrink sda4 to about 20GB (if it's much bigger)  give the extra space to /home.

Btw, sda5 & sda6 are logical partitions, not primary.

---

### Post by oldfred on 2011-04-05
+1 on Dutch70's suggestion of using sda6 as /home. I prefer smaller system partitions for both Linux & windows and keeping data separate from system. You can reinstall easier, but still need good backups of data.

To see what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Hedgehog1 on 2011-04-05
> ...I deleted my swap partition and converted that to an extended partition, I then grew it to a 100gb extended partition. I created 2 new primary partitions, one for swap and one for the OS... 

Good thinking - it can be something of a puzzle unless one of the primary partitions is swap; that gives a person 'wiggle room' :D

The partitions on your disk look like this (as seen on the disk):

[COLOR="Red"][B]sda1 - OEM System partition
sda2 - Windows 7
sda3 - NEW Extended partition
__sda5 - NEW Swap partition
__sda6 - NEW OS Partition
sda4 - old OS partition[/B][/COLOR]

Dutch70 and oldfred had suggested using a separate partition for your '/home'.  I do this as well on my Ubuntu systems.  It separates the OSes 'Stuff' from my 'Stuff' (I am using my big words here, 'Stuff' :D ).

So I am going to suggest some options based on a seperate '/home' and also the simpler 'everything in one' partition.

Everything in one:

1) Delete sda4.
2) Resize extended partition sda3 to reach the end of the disk.
3) Resize logical partiton sda6 to reach the end of the disk, too.

[COLOR="Red"][B]sda1 - OEM System partition
sda2 - Windows 7
sda3 - NEW Extended partition
__sda5 - NEW Swap partition
__sda6 - NEW BIGGER OS Partition[/B][/COLOR]


Dutch70 suggestion:

Re-purpose sda4 to be your '/home' partition:

[B][COLOR="red"]sda1 - OEM System partition
sda2 - Windows 7
sda3 - NEW Extended partition (shink to just fit sda5 & smalled sda6)
__sda5 - NEW Swap partition
__sda6 - NEW OS Partition (20 gigs for OS only)
sda4 - NEW '/home' partiton to the end of the disk[/COLOR][/B]

And finally another variation just to confuse you:

[B][COLOR="red"]sda1 - OEM System partition
sda2 - Windows 7
sda3 - NEW Extended partition (resize to reach the end of the disk)
__sda5 - NEW Swap partition
__sda6 - NEW OS Partition (20 gigs for OS only)
__sda7 - NEW '/home' partiton to the end of the disk[/COLOR][/B]


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-05
You were asking how to mount the /dev/sda4 partition, weren't you? :oops:

First create a directory that we will 'overwrite' with a mount command:

```
sudo mkdir /media/hedgehog
```

Then 'Mount' the partition to be used whenever you ask for '/media/hedgehog':

```
sudo mount /dev/sda4 /media/hedgehog
``` 

***The Hedge***

:KS

p.s. To have a partition mounted at boot up, we change the fstab file; like this:

[IMG]http://img840.imageshack.us/img840/4129/laptophd.png[/IMG]

The partition can be on the same hard drive, or a different one.

---

### Post by Dutch70 on 2011-04-05
> Dutch70 suggestion:

Re-purpose sda4 to be your '/home' partition:

sda1 - OEM System partition
sda2 - Windows 7
sda3 - NEW Extended partition (shink to just fit sda5 & smalled sda6)
__sda5 - NEW Swap partition
__sda6 - NEW OS Partition (20 gigs for OS only)
sda4 - NEW '/home' partiton to the end of the disk

My suggestion was actually to keep sda4 as his OS & resize it to about 20GB, if necessary. That way he keeps all of his settings, or he can do a fresh install if he wants. 

Then use sda5 & 6 *(the remainder of his hdd)* as /home & swap.
*(resizing the extended partition if necessary)*

---

### Post by psusi on 2011-04-05
Are you sure you chose to boot from sda6 from the grub menu?  Once you do, post the output of:

```
cat /etc/fstab /proc/cmdline /proc/mounts
```

---

### Post by MMDeveloper on 2011-04-05
Hey guys, sorry for the lack of updates. I stayed up kind of late last night working on this and finally got it fixed.

The reason I didn't make the sda4 (old linux OS partition) a /home directory was because I had plans to triple boot the laptop so I wanted to keep that old partition for the 3rd OS.

Knowing that I had all the files copied to the new partition, I felt comfortable deleting my sda4 partition, which of course eff'd up the grub install. I booted to a ubuntu live cd, re-installed grub

mount /dev/sda6 /mnt
grub-install --root-directory=/mnt /dev/sda

rebooted, viola, all fixed. So I guess it was just a grub issue that was causing my problems. From there I installed Backtrack as my 3rd os, which of course re-installed grub legacy, which caused ubuntu to not work again. A quick boot to a ubuntu cd to re-install grub2 fixed the issue.

Now it's triple booted.


So for the overall reason for my problems, I just needed to re-install grub, instead of trying to simply "update-grub". That fixed all my issues.

/sda1 - OEM partition
/sda2 - Win7
/sda3 - extended partition
-- /sda5 - shared swap
-- /sda6 - ubuntu 10.10
/sda4 - Backtrack 4r2

sda4 and sda6 both share the same swap partition, figured since only one will be booted at any given time, I didn't see any harm in it.


---edit
and I want to thank ALL of you for your prompt responses. Had I been freaking out less and checking the board more I'm sure following your suggestions would have led to an earlier bed time for me last night.

---

### Post by Dutch70 on 2011-04-05
Glad to hear you got it worked out. Having only one swap partition was a good idea.

Just to let you know, if you ever want to do more than a triple boot, you can have more than 60 logical partitions. Not that you'd ever want that many, just saying, it's possible. 

Have a look at my hard drives. :D

---

### Post by Hedgehog1 on 2011-04-06
> **Dutch70 said:**
> Just to let you know, if you ever want to do more than a triple boot, you can have more than 60 logical partitions. Not that you'd ever want that many, just saying, it's possible. 

Have a look at my hard drives. :D

Now you are just showing off Dutch70! :P

***The 'jealous' Hedge***

:KS

---

