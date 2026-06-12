---
title: "Benifits of diffrent partitions for /boot /home /tmp /usr /var /srv /opt /usr/local?"
date: 2009-11-23
forum: General Help
---

### Post by TheOnlyMrK on 2009-11-23
I just reinstalled Ubuntu 9.10 to save myself the time and headache of moving /home and /tmp from their default position to where I want them but when I got everything moved around I noticed their were a lot more "/" folders that I could put on their own partition. I ended up setting up my computer like this...

Hard drive 1 - 150GiB
/boot - 1GiB
/ - fill drive

Hard drive 2 - 80GiB
swap - 10GiB
/tmp - fill drive

Hard drive 3 - 1TiB
/home - fill drive

Yeah I'm probably going to be laughed at for the 1GiB /boot and definitely the 10GiB swap but the /boot I couldn't find a recommended size for it on Google, and swap I figured why not since I have the room.
But I'm still curious of what the benefits of putting /usr, /var, /srv, /opt, and /usr/local, on their own partitions is, mainly because I don't know what these folders are. So could someone explain? Or link me to something that would explain a bit better. Either would be a great help.
Ever since the day I started using Linux/Ubuntu how the filesystem is organized always confused me, now I'm finally starting to figure it out, I used to laugh when people said it was better organized then Windows, now I see they're right.

---

### Post by aaronchall on 2009-11-23
I'm interested to see the response to this as well.  I thought the recommendation for a separate partition was really just for the /home directory. - Aaron

---

### Post by dcstar on 2009-11-23
> **aaronchall said:**
> I'm interested to see the response to this as well.  I thought the recommendation for a separate partition was really just for the /home directory. - Aaron

Yep, unless you want to waste your time for tiny performance improvements - at the cost of wasting disk space - then a separate /home is all 99.99% of people need.

Then again, these forums are full of posts by people who keep trying to get 0.01% performance increases and then wail "Help me - my system is broken"........

---

### Post by falconindy on 2009-11-23
There's more than one reason to make a separate partition for a directory.

**Containment:** Suppose you make a partition for /tmp. You're running some homegrown program that writes to tmp for intermediate output. However, your program runs into an infinite loop that causes it to start writing far too much junk out to the filesystem. If /tmp wasn't contained, it could bring down the entire system.

**Filesystem Preference:** Ext is great because its tried and true as far as stability, but its average when it comes to file handling performance. ReiserFS handles small files exceptionally well and would be very well suited for a directory like /var or /etc. On the other hand, you wouldn't necessarily want it for a directory full of video files. XFS would be much better suited for that as it excels in handling larger files and larger drives.

**Necessity:** In some cases, you NEED /boot on a separate partition. If your system runs on LVM and/or MDADM, the simplest way to deal with this is to put a simple filesystem such as Ext2 or ReiserFS on a small partition and place the bootloader there.

**Redunancy:** In addition to any of the above solutions, redundancy is always a valid reason. Separation not just logically, but physically, can be extremely valuable depending on your application. Much like general end users can be inclined to separate their /home out, a database admin might choose to separate /var (where mysql data resides) from the rest of the system.

Of course, adding more partitions and/or drives increases the complexity of the setup and can also increase your liability and risk for data loss.

---

### Post by UranUtan on 2009-11-23
Hi,

Here is what I learnt:

/boot just need 100 MB and I read somewhere that ext2 is more suitable for /boot as it doesn't need a journaling file system.

/ (root) 10 GB, ext4

/home, ext4, remaning storage. 

Personally I use all extra HD to mount extra folder directly in the root like /MyData1 /MyData2 (in ext4).

In my current machine, I have created a few dedicated partitions for /tmp /usr /usr/local /var all in ext4. Honestly I don't see any difference.

The best clues I still learn is actually in this post itself from the previous poster falconindy. Use ReiserFS for /var and /etc and XFS for partitions containing large files. I will try this next time. Thanks.

---

### Post by TheOnlyMrK on 2009-11-24
> **dcstar said:**
> Yep, unless you want to waste your time for tiny performance improvements - at the cost of wasting disk space - then a separate /home is all 99.99% of people need.

Then again, these forums are full of posts by people who keep trying to get 0.01% performance increases and then wail "Help me - my system is broken"........
Most people also know that adding up many small performance increases will turn into a big one. x3
But as far as the comment you were replying to, for anyone using Ubuntu for general use should only move the /home because personal files do not belong on a partition/hard drive with system files, the rest are for the more advanced and you probably wont get much benefit unless you know absolutely what to tweak. Obviously since I'm the one that started this thread to ask this question I don't know much more then you do at the minute so I'll wait for others to back me up on that.

---

### Post by jacobs444 on 2009-11-24
honestly there is no performance benifit, unless you are using different disks for each partition. Actually and this is factual, you take a performance hit when you do this on the same drive. There is one other benefit, and that is that putting /boot on its own, and the first of all partitions, you can access all of a drive that is too big for an older bios to support.

---

### Post by TheOnlyMrK on 2009-11-24
> **falconindy said:**
> There's more than one reason to make a separate partition for a directory.

**Containment:** Suppose you make a partition for /tmp. You're running some homegrown program that writes to tmp for intermediate output. However, your program runs into an infinite loop that causes it to start writing far too much junk out to the filesystem. If /tmp wasn't contained, it could bring down the entire system.

**Filesystem Preference:** Ext is great because its tried and true as far as stability, but its average when it comes to file handling performance. ReiserFS handles small files exceptionally well and would be very well suited for a directory like /var or /etc. On the other hand, you wouldn't necessarily want it for a directory full of video files. XFS would be much better suited for that as it excels in handling larger files and larger drives.

**Necessity:** In some cases, you NEED /boot on a separate partition. If your system runs on LVM and/or MDADM, the simplest way to deal with this is to put a simple filesystem such as Ext2 or ReiserFS on a small partition and place the bootloader there.

**Redunancy:** In addition to any of the above solutions, redundancy is always a valid reason. Separation not just logically, but physically, can be extremely valuable depending on your application. Much like general end users can be inclined to separate their /home out, a database admin might choose to separate /var (where mysql data resides) from the rest of the system.

Of course, adding more partitions and/or drives increases the complexity of the setup and can also increase your liability and risk for data loss.
Thanks, that really gave me a whole different view on why someone might partition up their hard drive, I was always just figuring it was performance thing and the only one to be on a different partition for safety reasons would be /boot, never considered the /tmp part.

---

### Post by oldfred on 2009-11-24
falconindy explanations are all good, but apply primarily for servers and very advanced users. The average user will work quite well with the standard install all in one partition and swap. With the old MBR partitioning of only 4 primary partitions you could not have a lot of partitions. Now with an extended partition you can have many more.

I have had a standard install for 3 years with some data in different partitions. I have so much cruft that I now want a clean install of Karmic so I am creating new data and /home partitions. I still am not sure I even want a separate /home since only configuration files and some misc. data will be in it and it should be easy to back-up next time I want a clean install. I also have a separate partition for grub as I like to chainboot into the various installs that I have. I see for me no advantage for any other system partitions.

---

### Post by Agent ME on 2009-11-24
If you want to separate different folders into partitions, and/or want to be able to freely combine several hard drives' worth of space into one partition, check out LVM. You can set it up easily on the alternate install disk. LVM lets you resize partitions and spread partitions over several hard drives (even let a single partition go over several hard drives).

---

