---
title: "Will home folder appear correctly when upgrading?"
date: 2011-07-21
forum: General Help
---

### Post by ragiete on 2011-07-21
I installed Natty on an empty hard drive, with different partitions. The drive is divided in three parts; a 10 GB swap partition (sda1), a 240 GB partition for Natty (sda2), and a 750 GB partition for the homefolder (sda3). When I check /home, I see there is a folder named 'ragiete', which of course is my home folder.

I am wondering about something though; when I'll install a fresh Ubuntu installation (Oneiric when it comes out), and I enter 'ragiete' as my username again, will the new installation use that same folder again (the folder isn't encrypted so that won't give any problems), or will it create a new one?

I hope it does use the already existing folder, because I want to keep using that same home folder after upgrading to newer versions of Ubuntu. I assume it will seeing as I'll keep the same username, but I just want to know for sure. :)

Thanks in advance!

---

### Post by TeoBigusGeekus on 2011-07-21
Putting the same username does not make ubuntu use the same home folder on a new installation.
While installing, at the partitioner stage, you have to choose manual partitioning, select your preferred existing home partition and give /home as its mount point; it's the only way to be done.

---

### Post by ragiete on 2011-07-21
> **TeoBigusGeekus said:**
> Putting the same username does not make ubuntu use the same home folder on a new installation.
While installing, at the partitioner stage, you have to choose manual partitioning, select your preferred existing home partition and give /home as its mount point; it's the only way to be done.

Yes, that is what I'd do. When doing a new install, I would again put sda2 as / and sda3 as /home. Seeing as the folder 'ragiete' is still on sda3, Ubuntu will use it when using 'ragiete' as my username again, right?

---

### Post by drs305 on 2011-07-21
And make sure the 'format' tick box for the /home partition is **not** selected...

---

### Post by ragiete on 2011-07-21
> **drs305 said:**
> And make sure the 'format' tick box for the /home partition is **not** selected...

Yeah, otherwise all data on the partition would be gone. :D

Thanks for the replies!

---

