---
title: "Merging partitions"
date: 2011-01-15
forum: General Help
---

### Post by rmcellig on 2011-01-15
You will notice from the attached file that SDS 6 is my main drive. I would like to somehow expand it to take up all of SDA 1. Is this possible? As I write this I am booted into the Ubuntu 10.10 installer CD.

---

### Post by Ocxic on 2011-01-15
No it is not possible, sda6 is an extended partition. and if sda1 is modified or deleted, you will lose sda6.

you will have to backup all your data, format and re-partition youR drive then copy all the data back. :(

---

### Post by Ocxic on 2011-01-15
No it is not possible, sda6 is an extended partition. and if sda1 is modified or deleted, you will lose sda6.

you will have to backup all your data, format and re-partition your drive then copy all the data back. :(

---

### Post by psusi on 2011-01-15
> **Ocxic said:**
> No it is not possible, sda6 is an extended partition. and if sda1 is modified or deleted, you will lose sda6.

you will have to backup all your data, format and re-partition youR drive then copy all the data back. :(

Ummm... no?

If you have enough space in sda1 to copy/move all of the files over that are currently in sda6, then you can delete sda5, 6, and 7, as well as sda3, then expand sda1 to use the free space.

---

### Post by srs5694 on 2011-01-16
First, Ocxic is misinformed on several points:


[list]
[*]/dev/sda6 is not an extended partition; it's a logical partition that resides within an extended partition (namely, /dev/sda3). This is a common error.
[*]Deleting /dev/sda1 will not affect /dev/sda3, /dev/sda6, or any other partition. (That said, if GRUB relies on files in /dev/sda1, your system might not boot any more after making this change.)
[*]To make the changes you desire, you don't need to back up everything; however, you may need to copy files from /dev/sda1 to /dev/sda6.
[/list]


Psusi is basically correct, although I think s/he misread your post; you'd need to copy from /dev/sda1 to /dev/sda6, not the other way around. It's not clear where you mount /dev/sda1 or how you do it, so I can't comment on the exact procedure and consequences of doing this.

Depending on your needs, though, I might recommend doing something different: IMHO, it's a good idea to use separate root (/) and /home partitions. This keeps your user data (in /home) safe from filesystem problems that might develop on the root (/) partition, and it enables you to easily wipe that partition and do a fresh installation (even of another distribution) without affecting your user data. Thus, you might want to leave the disks as-is, using /dev/sda1 as /home and /dev/sda6 as root (/). That said, /dev/sda6 is very large to serve as a root (/) partition, so you might consider shrinking it and moving it to the right, shrinking /dev/sda3 to move the free space out of the extended partition, and expanding /dev/sda1 to fill the gap. This procedure will take a while, though, and it poses some risks of data loss, so do it only when you have some time to spare and only after you've backed up your computer. [This site](http://www.psychocats.net/ubuntu/separatehome) describes the process in general, although it may be different for you, depending on how you're already using your partitions.

---

### Post by Ocxic on 2011-01-16
Sorry. srs5694 is right, I answered that very quickly..... follow his advise.

---

### Post by rmcellig on 2011-01-16
Thank you so much for all of your suggestions!! I learned a lot from all of this but in the end, I reformatted the drive and did a new install on one partition. This laptop is more for experimenting with and learning Ubuntu etc... My main computer (for now :)), is my iMac running OS X.

srs5694,
You mentioned that I should create a new partition for my home folder. Is that correct? This way like you said if something happens to the system partition, my data is OK. Do I somehow have to reset links to the new location of my home folder? I know that Ubuntu-Tweak allows you to do this. I think I may play around with creating a new partition to put my home folder in. 

Is there a video I might be able to look at that can show me how to do this?

---

### Post by srs5694 on 2011-01-17
Creating a separate /home partition is most easily accomplished at system installation; just select the manual partitioning option and set it up at that time. After the fact, it gets trickier. Follow the link I provided in my last post for a detailed description. There *must* be a video on YouTube describing this (there are far lamer videos there!), but I don't happen to have a link.

---

