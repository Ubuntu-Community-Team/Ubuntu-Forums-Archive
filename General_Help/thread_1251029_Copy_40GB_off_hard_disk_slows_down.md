---
title: "Copy 40GB off hard disk slows down"
date: 2009-08-27
forum: General Help
---

### Post by moored99 on 2009-08-27
First off I am a newbie to Ubuntu after 20+ years using Windows, and I love it. 

My server is setup with 2 x Intel 5430 CPU, 2 x 2TB drives setup as RAID 1 (boot) and 4 x 2TB drives as RAID 5 (Data), Ubuntu server, no lamp, but setup with GNOME GUI and VirtualBox.

My first problem is trying to configure the drives as a 6TB volume (4 x 2TB RAID 5 = 6TB) I know that I can do this under MS Server 2003 by setting the drive to GPT and I have tested that. I don't seem to be able to get past 1.46TB for the first partition and then 2TB and 2TB for the second and third volume I have tried using GPARTED as a bootable CD and through the GUI. I have tried ext3 and ext4 but no luck. any suggestions.


My second problem, I have mounted an external 2.5" notebook hard disk on an external ESATA card (1.5gbps), I am coping 40GB off the notebook drive (to back it up before I rebuild it) the copy started off at 25 MB/sec it is half way through and that speed has drooped to 9MB/sec, is that normal do I have a problem.

---

### Post by P4man on 2009-08-27
> **moored99 said:**
> 
My first problem is trying to configure the drives as a 6TB volume (4 x 2TB RAID 5 = 6TB) I know that I can do this under MS Server 2003 by setting the drive to GPT and I have tested that. I don't seem to be able to get past 1.46TB for the first partition and then 2TB and 2TB for the second and third volume I have tried using GPARTED as a bootable CD and through the GUI. I have tried ext3 and ext4 but no luck. any suggestions.

Found this on google:

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

Never even knew there was an issue with >2TB partitions..


> My second problem, I have mounted an external 2.5" notebook hard disk on an external ESATA card (1.5gbps), I am coping 40GB off the notebook drive (to back it up before I rebuild it) the copy started off at 25 MB/sec it is half way through and that speed has drooped to 9MB/sec, is that normal do I have a problem.

Not necessarily a problem I think. Small files will give you slower transfer speed, maybe its just copying a ton of small files now?

---

### Post by P4man on 2009-08-27
BTW that link mentions you have to recompile your kernel for EFI partition support, but it seems its included in ubuntu kernel since v6.06. So the rest might be outdated too, perhaps google for something more recent.

---

