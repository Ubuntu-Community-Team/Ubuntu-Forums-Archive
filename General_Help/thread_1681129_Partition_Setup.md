---
title: "Partition Setup"
date: 2011-02-03
forum: General Help
---

### Post by Lucrin on 2011-02-03
Okay I can't seem to find any definite place to find answers for this. I am setting up a linux partition with the following setup:

320gig hard drive
50 gigs linux, rest is windows data drive

Partitions:
/boot 200MB
SWAP 4gigs
/: 20 gigs
Home: 30 gigs
All of the partitions will have to be grouped under and extended partition because there are already other recovery partitions on the drive, is this ok?.

Now what I can't remember is which partitions should be primary and which should be logical? And for "Use As" what should I set for each? Obviously SWAP should be "swap area" but are the rest all just "Ext4 Journaling?"  Thanks.

EDIT: Also how do I know which device I should put the boot loader onto?

---

### Post by lindsay7 on 2011-02-03
Make the 50 gig partition an extended partition.  make a partition the root or "/" partition 10 gigs. this is where your system OS will go. Make a "home" partition of about 25 gigs, this is where all of your setting and other stuff will go. Make a "data" partition of about 11 gigs, this is where you can store Misc. stuff.  That leaves about 4 gigs for the "swap" partition.

You of course can adjust this as you see fit as this is just a suggestion.  Having a root partition lets you use this for future upgrades so that you only use this partition and leave the rest alone to save all of your data, etc.

---

### Post by oldfred on 2011-02-03
I pretty much agree with        lindsay7, but minor differences. Each of us has different opinions on partitioning. And after you use it for a while whatever you pick now will change. Every couple of years I find my partitioning is not correct and have to change it. And I have too much data, but then it is an excuse to buy a new larger drive.:grin:

You also do not need  a /boot unless you have a very old system, or a server with RAID or LVM. It makes things unnecessarily complicated.

I also do not like to directly write into another system's system partition as that can lead to issues. You also can see all the hidden files & folders in windows from Ubuntu so it is possible to accidentally move or delete some vital windows file.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended see below).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Also see this:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Note Known Issues section
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)


Installs:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

---

