---
title: "How to create a single logical drive out of two physical drives?"
date: 2010-03-04
forum: General Help
---

### Post by ryanils on 2010-03-04
Hi all,
 
I'm installing Ubuntu to be used as an NFS storage server for my VMWare ESX servers. I've got a server that has two 2TB drives in it. The hardware raid controller isn't an option because it only sees up to 1TB of each drive. So, I'm trying to figure out to do this using either LVM or Parted. I don't know much about doing this, and LVM was the first thing I tried but it didn't seem to do much. It looks like it just created a smaller partition to install Ubuntu on. It didn't ask me what I wanted to do with the rest of the drive space. I've messed around with Parted and am not sure what to do, to be honest. I found a few blog posts but most started off assuming that I knew how to get to where they were starting from.
 
Does anyone have either a suggestion, or know of a great blog post that talks about this? Or perhaps can somebody sum up how to do this in a nice concise response?
 
It's just two drives, /dev/sda /dev/sdb
 
Thanks in advance!

---

### Post by undecim on 2010-03-04
RAID 0 is a "striped" raid. It will put half the sectors of the logical 4TB drive on each 2 TB drive. Every other sector is on one drive, which makes drive operations faster. (if you need to read 4 consecutive sectors, for example, you read it in the time it takes to read 2 consecutive sectors from each drive).

The primary downside to a software-based RAID 0 is that it causes some CPU overhead. It's not much, barely noticable from what I've read.

---

### Post by ryanils on 2010-03-04
> **undecim said:**
> RAID 0 is a "striped" raid. It will put half the sectors of the logical 4TB drive on each 2 TB drive. Every other sector is on one drive, which makes drive operations faster. (if you need to read 4 consecutive sectors, for example, you read it in the time it takes to read 2 consecutive sectors from each drive).
 
The primary downside to a software-based RAID 0 is that it causes some CPU overhead. It's not much, barely noticable from what I've read.
 
Yea, a RAID 0 is what I would have used if my hardware raid controller was seeing all 2TB of each drive. It isn't though. :(
 
Using LVM or Parted, is RAID 0 still the terminology I'd be looking for? How do I create a software-based RAID 0?

---

### Post by ryanils on 2010-03-04
Oh, wow. I somehow managed to not see the "Manual" partitioning option. The software raid setup is in there. :(

---

