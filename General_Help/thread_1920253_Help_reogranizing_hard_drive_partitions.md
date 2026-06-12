---
title: "Help reogranizing hard drive partitions"
date: 2012-02-04
forum: General Help
---

### Post by nphls on 2012-02-04
[SIZE="3"]**[BACKGROUND INFORMATION]**[/SIZE]

So it's like this. 

I was what might be called a Windows user until some months ago, when I started using Ubuntu. I tried it out for a some months and now I use it as my main OS, I just boot into Windows when I need some application that wine really can't handle (e.g Visual Studio, Enterprise Architecht, etc)

The problem I have now is that my hard drive partitions look like this, a total mess:

[IMG]http://i39.tinypic.com/2yy85kw.png[/IMG]

the sda1 partition, the recovery partition, I intend to leave it, no problem there.

the sda2 partition, the Windows OS partition, I intend to leave too. 75GB might be a little excessive if I don't intend to use very often, but that's ok.

the sda3 partition, has partitions inside them... i didn't know this was even possible. this is were my quetions start:


**[SIZE="3"][QUESTIONS][/SIZE]**

1. what's the best solution to store my media in ubuntu? to have a large partition (200gb) or have like 50gb for system and 150gb for media, or doesn't it even matter?

2. what format should i format this partition so that I can access it from windows if I want?

3. is it possible to do all this without having to reinstall ubuntu and loose all my configurations?

4. i was told that linux-swap partition should have around two times the RAM of the computer. Since mine has 4Gb the linux-swap should have 8gb, is this correct? If so, can I merge the two partitions? How?



Thanks in advance for your help ;)

---

### Post by Ms. Daisy on 2012-02-04
I wouldn't call that a total mess. Not sure why you have two linux swap partitions & the unallocated space, but the rest looks OK.  

You may benefit from reading up on how partitions work. You can only have 4 partitions on a hard drive. sda3 is an extended partition (partitions inside of a partition) so that it is possible to have more than 4. Ubuntu has installed itself inside of an extended partition on all the computers I put it on. 

Regarding the size of Ubuntu's swap, see this [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)  It looks like 2x the RAM might be a dated piece of advice.

Whatever you choose to do, definitely back up EVERYTHING before you mess around with the partitions.

---

### Post by JKyleOKC on 2012-02-04
> **nphls said:**
> the sda3 partition, has partitions inside them... i didn't know this was even possible.I'll only address this part of your questions. The partition table in the MBR (Master Boot Record) of any hard drive/SSD that's formatted to be MS-DOS compatible has space for only four entries. Because of this, the "extended partition" was invented when hard disks became big enough to need more. It uses only a small space that provides room for additional entries, but reserves a much larger space in order to prevent any other entry in the MBR's table from taking it.

The four partitions inside the MBR's table are numbered 1 through 4, even if not all of them exist. Yours, for example, is sda3 and you have no sda4. Partitions contained in an extended partition begin numbering at 5 and are known as "logical" partitions. However they have all the same characteristics as the four primary partitions; the operating system reads information from the partition table(s) during the boot sequence and keeps it in RAM for the rest of the session, so programs don't even know which kind of partition they are using.

EDIT: On second thought, I'll also address your media storage question. You already have a fair-sized partition, more than 100 GiB, storing data for Windows. You can read and write to this partition from Ubuntu also, although you might need to edit your /etc/fstab file to get write permission to it since NTFS areas are treated a bit differently by Ubuntu. It doesn't have a lot of free space left, but it's possible to free up some space in the adjacent partition and merge that in. Doing so is a bit tricky, and cannot be done when the hard drive is in use -- which means you have to run from the Live CD to make any changes. As Ms. Daisy has said, be sure to back up everything you want to keep before making any changes to the partitions! If you can live with the present size of sda5 for use by both systems, I'd recommend leaving it all alone for now.

---

