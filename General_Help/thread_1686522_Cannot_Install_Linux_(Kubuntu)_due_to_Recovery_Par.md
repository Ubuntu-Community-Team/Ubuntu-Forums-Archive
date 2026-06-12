---
title: "Cannot Install Linux (Kubuntu) due to Recovery Partitions"
date: 2011-02-12
forum: General Help
---

### Post by HappySquirrel on 2011-02-12
Hi All,

I am an almost completely new user of Linux, and all my experience consists of a month of Kubuntu on a netbook, which I eventually got used to and much prefer to Windows.

I know it's probably not good etiquette to ask for help in my first post, and this is probably the wrong place but...

Basically, my Acer Aspire Z5700 came with Windows 7 Home Premium, which I do not want to lose - instead I want to dual boot with Kubuntu.

I have heard that Ubuntu cannot install onto a 5th partition, and my HDD is already Partitioned 4 times (WIndows C: drive, ~16GB Recovery Partition, Windows SYSTEM RESERVED 1GB Partition??, and some strange 1MB partition). I do not know what the 1MB partition is , and was wondering if I could delete one of these partitions or something to install Kubuntu,

Kubuntu recognises the unpartitioned space as "free" but "unusable" :(

Sorry for the long, and probably annoying, question and thanks in advance

---

### Post by Habeouscorpus on 2011-02-12
You'd have to convert one to an extended partition, to fool the disk into thinking there's only four. Then you could split the extended partition in chunks. Windows will not boot from an extended. However, I am unsure how to do that on your setup. You could always use clonezilla to copy a partition and save it somewhere.

Or, you could take a chance and delete the 1 MB. 1 MB is very, very small and not much would fit on it. But it could be an important partition, so I don't recommend this.

---

