---
title: "Problem with a Fake RAID"
date: 2009-11-05
forum: General Help
---

### Post by Camicia on 2009-11-05
I am trying to install a ***Ubuntu 9.10*** *server* *64bit* on a machine **without** OS.
 
I bought a motherboard *Foxconn P55A-S* ([[COLOR=#444444]http://www.foxconnchannel.com/Produc...d=en-us0000473[/COLOR]]("http://www.foxconnchannel.com/Product/Motherboards/detail_overview.aspx?id=en-us0000473")) that has a Marvell 88SE6121 controller (88SE61xx series).
 
The motherboard has a RAID support (atl east I thought) so could guarantee me that my data are safe if one HD dies. I would like to be able to replace that HD and expect that automatically or with a simple tool, I would be able to restore the system with all the HDs integer. I would also expect an increase in performances.
 
I have **4 HDs by Hitachi Deskstar 500Gb each \\:D/**. I was thinking about using 3 of them in RAID 5 and 1 of them as a spare (maybe as a backup device for now).
 
I set up in the BIOS "Configure SATA as" -> "RAID". then pressing Ctrl-I, I could then access to an extended BIOS during the BIOS where the Intel (R) Rapid Storage Technology pop up. 
 
First time, I set up a** RAID 5** with the first 3 disks.
 
During the installation of Ubuntu 9.10 Server, it said that a RAID has been recognized and if I want to use it. However in this case only the 4th HD (the spare one) is displayed.
 
Looking on the Internet, I realized that the Marvell 88SE6121 is a **"fake" Raid** (the operations are run by the CPU). :-k
 
I found that Intel® Matrix Storage Manager (and I am not sure that it is completely related what I own) does support only RAID 1 and 0. So I decide to give it a shot with a RAID 1+0.
 
I reconfigure a **RAID 0+1** and this time the installation show me that I have 2 volumes of 500GB each (instead of one of 1Tb as expected). 
 
Trying to do something with one of the displayed drive I ended up with some partitions that I don't know how to delete. Plus **the installation hung up on formatting one of this partition** (showing 33% and not progressing for at least 15 min).
 
**What do I want?**
1) Deleting the partition created on the first of the 2 drives in mirroring. I am not sure how you can do that from the installation.
2) Most important: Being able to take advantage of data redundancy of a RAID 1 or (better) RAID 5. Then it is nice to have: increased performance from RAID 0/1. 
 
How do I get it to work?
 
Thank you in advance,
Camicia ):P

---

### Post by Giblet5 on 2009-11-05
Software raid is the shortest path to data loss.

It looks good on paper (or cardboard, if you're reading a motherboard's packaging), but it's a Very Bad Idea in practice.

I recommend NOT using software RAID.

RAID is great. If you want that, then buy a hardware RAID controller. Adaptec has a spectacular PCIe card that uses SATA drives. It's very fast. I recommend RAID 10 (aka 0/1, 1/0). RAID 5 is slow and offers no real benefit over RAID 1.

---

### Post by Camicia on 2009-11-05
If the driver is well written, it should not have any problems. 
Or are you saying that so far the software and fake RAID drivers are not stable in Linux? I  didn't hear any dreadful stories about FakeRAID on Window.

Do you have expereinces with data loss on SW RAID?
Does anybody here have experence on a successful software RAID installation?

---

### Post by Giblet5 on 2009-11-05
> **Camicia said:**
> If the driver is well written, it should not have any problems. 
Or are you saying that so far the software and fake RAID drivers are not stable in Linux? I  didn't hear any dreadful stories about FakeRAID on Window.

Do you have expereinces with data loss on SW RAID?
Does anybody here have experence on a successful software RAID installation?

[See for yourself]("http://www.google.com/search?q=software+raid+sucks&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

It's not that the available linux raid software isn't well written - it is - it's just that software raid is like building a luxury fortress inside an active volcano's caldera.


If you change your mobo, or use a different sw raid chip, your data is gone. If the raid software changes technique, your data is gone.

However, if you never touch any of the hardware, and it never breaks, and if you never install updates, and if you never upgrade OSes again, then you should be golden.

---

### Post by Camicia on 2009-11-05
What about a soft RAID 1? Does it have the same kind of problems?

---

