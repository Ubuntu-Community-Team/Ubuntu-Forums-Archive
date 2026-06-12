---
title: "install partitioning problems"
date: 2006-05-05
forum: General Help
---

### Post by sgusev on 2006-05-05
Hello, I've been trying to install Kubuntu and Ubunutu and have run into problems with partitions. I have a SATA haddrive running through a PCI SATA Controller Card. I initially tried the following partition setup
512MB swap -bootflag off
20GB ext3 root ("/") -bootflag on
30GB FAT32 ("/var") -bootflag off

The FAT32 is intended for shared space for an impending Windows XP install, I left about 30Gig unpartitioned for this as well. Under this setup, I was getting constant deboostrap errors with 5 different CD's (tried botu ubuntu and kubuntu) all md5 hashed. However, when I let Ubuntu setup the partitions on its own, i.e. partition all of the free space. I ran into no problems, even with a bootdisk that had generated errors just moments prior.

I'm pretty new to Linux, so was this partition method incorrect? If so, now that I have Ubuntu installed on the whole drive, how do I go about properly partitioning both a FAT32 shared partition, and leaving empty space for my XP install.

Thanks for the help.

---

### Post by rcarring on 2006-05-05
I was going to suggest that you install XP first

Hard disk 60GB -- allow for XP -- 30GB -- install XP first...
Free space 30GB left

Install Ubuntu into freespace and allow it to partition this freespace.

This is how I dual booted between XP and SUSE9 for a long time.

with a much smaller hard drive though.

---

### Post by sgusev on 2006-05-05
okay, i guess i'll give that a try. I've been trying to do it through GParted but it doesn't even give me the option to resize the partition.

---

