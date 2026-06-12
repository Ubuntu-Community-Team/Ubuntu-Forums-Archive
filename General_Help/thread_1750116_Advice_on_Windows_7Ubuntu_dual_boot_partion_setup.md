---
title: "Advice on Windows 7/Ubuntu dual boot partion setup?"
date: 2011-05-05
forum: General Help
---

### Post by elsmandino on 2011-05-05
Hi there,
 
I tried Ubuntu out for the first time in years and have decided to give Linux another try.  I ran the latest version (11.04) from a USB stick on my laptop and liked it so much that I want to install it as a dual operating system.
 
My laptop is a Samsung R580 which has 4GB Ram and a 500GB HDD.  Windows 7 needs to be reinstalled.
 
Can anyone advise what the best setup for dual operating systems on this computer should be?
 
At them moment, I was thinking:
 
Partition 1: Windows 7 (40GB)
Partition 2: Ubuntu (10GB)
Partition 3: Ubuntu Swap File (8GB - twice my Ram Size)
Partition 4: General NTFS partition for storage that can be used by both operating system (Size - everything left)
 
Can anyone give me any advice on the above?
 
Thanks very much.

---

### Post by ububeginner on 2011-05-05
How big are you planning on having the General NTFS partition?
The reason I ask is that I think that your Ubuntu partition could use more space to grow in the future
I had a very similar setup and then needed to grow Ubuntu, and then this happened:

[http://ubuntuforums.org/showthread.php?t=1749195](http://ubuntuforums.org/showthread.php?t=1749195)

I don't know if this is the direct result from resizing the partitions but this kind of editing can be risky and therefore I think you should allocate enough space to Ubuntu from the start.

---

### Post by satanselbow on 2011-05-05
I would be more generous with you W7 partition, maybe a 60GB minimum. You be the judge but you want to give yourself a little headroom and given you have 500GB to play with there is little point leaving yourself short and having to move huge amounts of data later.

If you are hanging onto W7 for gaming or Graphic Design (CS5 = 10GB+) purposes you have to remember that the space requirements are gonna be pretty heavyweight.

I would also suggest splitting your remaining space in 2 and having an ubuntu specific /home partition on ext4 and then a "backup" or "data" partition as NTFS that either system can read and access without it directly being part of the system of either. Reduces the risk of inadvertently messing with systems files or the config of one while using the other - and gives, albeit weak - as it is all on the same physical drive, backup by duplication 

W7 will likely use 2 primary partitons at the front of your drive - and should always be installed 1st. You can then create an extended partiton (with Gparted on a LiveCD) with logical partitions (ext4) for /home /root and /swap. *** I use the /home, / (root), /usr, /var method at the mo but that is not essential or necessary *** 

Put your NTFS backup (primary partition) - if you want to go that way right at the end of the drive.

Always create you Ubuntu /home partition the 1st logical partition so you can delete the partitions above it without problems later (upgrading / changing distro etc) and it is usually good to have your linux-swap somewhere in the middle of the drive for the best of both worlds speed wise ;)

This is my current drive layout and allows me put distros on and off as required :D

/sda1 + 2 are W7 (if and when I next reinstall W7 is will reduce it to 1 part anyway)
/sda3 is the extended "container" housing

/sda5 as my regular stable 10.10 /home (can/will be used for 11.04 if and when I take the permanent plunge - which is debatable.)

/sda6 is linux-swap @ 2 X RAM (ie I got 3GB at the mo)

/sda 7,8,9 are my 10.10 installation

/sda10 is my 11.04 testing/sandbox

/sda4 (currently ext4 although does get wiped and reformatted to NTFS sometimes for shareability) is a backup of my 10.10 /home

[IMG]http://i55.tinypic.com/28gvvj7.jpg[/IMG]


There are numerous ways of doing it - and hopefully you will get more schema or suggestions which way to go but this is the time tested way I go about things. Makes dropping in new distros etc simple without having to move huge amounts of data about.

For example Fedora 15 is due at the end of the month and I will not be able to resist :D Shrink down /sda10 in gparted - create another logical partition and away I go! No hanging about pointlessly moving GB of data :popcorn:

---

### Post by elsmandino on 2011-05-05
Hi there,

Thanks very much for the responses.  You are definitely right, I think I need to look at the size of partitions a bit more closely.

Say I did use just four partitions for the time being, am I correct to put them in this order:

1: W7
2: Linux
3: Linux Swap File
4: Shared Partition

Or would it be better to put the shared partition in the middle and have the operating systems either side?

e.g. 
1: W7
2: Shared Partition
3: Linux
4: Linux Swap file

or does it ultimately not matter that much?

Also, am I right in thinking that I can use a NTFS shared partition between ubuntu and Windows 7?  I remember that years ago, it was unsafe for Linux to write to an NTFS partition.

Thanks again

---

### Post by satanselbow on 2011-05-05
The exact locations of the Shared NTFS partition is not so important - although I would consider there the be (slight) performance gains for Ubuntu/Linux by being nearer the top of the drive - ie push the NTFS share to the end.

I really would suggest a separate /home partition for Ubuntu/Linux.

It really does make life so much simpler and safer to separate your data (which is the real important stuff!) from the OS. With a separate partition you can go mad testing distros left right and center safe in the knowledge that nuking the system isn't gonna take your family photos and music collection with it ;) Step down off soapbox and relax...  

*Edit* Ever wondered why google is over run with "Windows crashed and I've lost my data" type forum posts ;) *Edit Over*

With that in mind the real one to watch though is the internal order of the Extended partition. If you put your /home in 1st you will never have to move it again. To keep things simple and minimilistic 20GB for / (root) and your 6GB for /linux-swap is all else you would need.

If you plan to pump most of your data into the shared NTFS then you can make your own judgements as to how big /home need be (having the luxury of an unrestricted fatpipe I can go pretty mental downloading at times and have a few DVDs worth of FLAC music + Distro ISOs + movies for the kids etc etc) Give it a bit of thought ;)

:popcorn:

---

### Post by satanselbow on 2011-05-05
> **elsmandino said:**
> Also, am I right in thinking that I can use a NTFS shared partition between ubuntu and Windows 7?  I remember that years ago, it was unsafe for Linux to write to an NTFS partition.

Thanks again

Sorry - missed that bit ;)

No problems reading/writing to/from NTFS for quite a while AFAIK :D

---

### Post by ububeginner on 2011-05-05
> I remember that years ago, it was unsafe for Linux to write to an NTFS partition

I don´t remember years ago, but I suspect that what was meant is that it is unsafe to work with files located on a partition that also houses an OS, while working on a different OS, regardless of the filesystem. That would still apply today. 
There is nothing wrong with having a seperate NTFS partition shared between Win and Ubuntu, in fact it´s probably what most dual booters do.

---

### Post by satanselbow on 2011-05-05
> **ububeginner said:**
> I don´t remember years ago

:popcorn:
A good point - well made :D

I've kind of gone out the other side and struggle to remember the last 10 minutes :(

---

### Post by oldfred on 2011-05-05
I used FAT32 for my shared partition with XP back in 2006. But bought a new drive and converted to NTFS when installing 9.10. I have not had any issues that I know of.

With 500GB I would make / (root) 20 or 25GB. With 4GB of RAM you only need 4+ (in MiB) if you want to hibernate. But Ubuntu boots so fast that I do not hibernate. 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you ever think you might want to try other systems, or even test the next install without messing with your current install an extra 20GB partition or two is handy.

Just realize that whatever you think is your optimal partitioning scheme is, will not be what you want later. I find my optimal has changed a lot as time goes by, but I afford the luxury (necessity/reliability) of a new drive every 2 or 3 years and then can reorganize.

---

