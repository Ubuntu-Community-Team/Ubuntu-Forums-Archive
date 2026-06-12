---
title: "Will this..."
date: 2011-02-11
forum: General Help
---

### Post by Ubntu on 2011-02-11
Dual-Boot?

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

Shrink free space, then use it to install Ubuntu or GNU/Linux in general.

---

### Post by DanneStrat on 2011-02-12
> **Ubntu said:**
> Dual-Boot?

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

Shrink free space, then use it to install Ubuntu or GNU/Linux in general.

Yes, you can do it as shown in the video.

First I would recommend you backup your personal files.

Then you can shrink the volume.

For a little more detailed info on dual-booting, see this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Ubntu on 2011-02-12
> **DanneStrat said:**
> Yes, you can do it as shown in the video.

First I would recommend you backup your personal files.

Then you can shrink the volume.

For a little more detailed info on dual-booting, see this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Great! How much should I shrink?

---

### Post by DanneStrat on 2011-02-12
> **Ubntu said:**
> Great! How much should I shrink?

That depends on what you will be doing with your

ubuntu installation and how much disk space you can afford to 

give.

A ubuntu installation will take about 4 GB of

disk space. Then you need room to install new packages and

store your personal files. If you don't plan on

storing large files in ubuntu, I would say

you shrink that volume so that you have approximately

20-30 GB unallocated free space. If you do plan on

storing large files you should go bigger.

It all depends on what you're willing to give.

Then follow the tutorial on that youtube

link and you will be good to go!:)

---

### Post by DanneStrat on 2011-02-12
Double post.

---

### Post by Ubntu on 2011-02-12
> **DanneStrat said:**
> That depends on what you will be doing with your

ubuntu installation and how much disk space you can afford to 

give.

A ubuntu installation will take about 4 GB of

disk space. Then you need room to install new packages and

store your personal files. If you don't plan on

storing large files in ubuntu, I would say

you shrink that volume so that you have approximately

20-30 GB unallocated free space. If you do plan on

storing large files you should go bigger.

It all depends on what you're willing to give.

Then follow the tutorial on that youtube

link and you will be good to go!:)

Alright, I am thinking about 70GB. Hope everything goes well.

---

### Post by DanneStrat on 2011-02-12
> **Ubntu said:**
> Alright, I am thinking about 70GB. Hope everything goes well.

70 GB will be plenty of room.

I can give you a tip on how a

good partitioning could be:


With 70 GB you could have

a "/"(root) partition size of 10-15 GB (10 GB will be large enough in most cases)

a swap partition approximately 2x the size

of your ram memory(If you have 512 MB ram you make swap 

partition 1024 MB).

Then you can make a /home partition with the remaining

free space.

---

### Post by Ubntu on 2011-02-12
> **DanneStrat said:**
> 70 GB will be plenty of room.

I can give you a tip on how a

good partitioning could be:


With 70 GB you could have

a "/"(root) partition size of 10-15 GB (10 GB will be large enough in most cases)

a swap partition approximately 2x the size

of your ram memory(If you have 512 MB ram you make swap 

partition 1024 MB).

Then you can make a /home partition with the remaining

free space.

I shrunk it, but Ubuntu wouldn't load. :/ So I tried Linux Mint, and it so the free space could not be used. Help.

---

### Post by DanneStrat on 2011-02-12
I had a closer look at the article i gave you earlier about

dual-booting and found this:

"After shrinking the Windows partition, you should reboot once (or twice) into Windows prior to installing Ubuntu (or using GParted). This allows the Windows system to automatically rescan the newly-resized partition (using chkdsk in earlier versions or a similar utility in later versions) and write changes to its own bootloader configuration files.

If you start mucking around with other partitions before Windows has a chance to reset itself, the Windows bootloader will not be able to read the partition table properly (and will therefore refuse to boot entirely). If this happens, you may later have to repair the Windows partition bootup files manually using the Windows Recovery Console."


Reboot your computer a couple of times and then boot with the 

live cd and try partitioning again. It should work.

---

### Post by DanneStrat on 2011-02-12
I forgot to ask, did you check

the md5 hash of the .iso

you downloaded? It's very important

that your install media isn't corrupted.

---

### Post by Ubntu on 2011-02-12
> **DanneStrat said:**
> I had a closer look at the article i gave you earlier about

dual-booting and found this:

"After shrinking the Windows partition, you should reboot once (or twice) into Windows prior to installing Ubuntu (or using GParted). This allows the Windows system to automatically rescan the newly-resized partition (using chkdsk in earlier versions or a similar utility in later versions) and write changes to its own bootloader configuration files.

If you start mucking around with other partitions before Windows has a chance to reset itself, the Windows bootloader will not be able to read the partition table properly (and will therefore refuse to boot entirely). If this happens, you may later have to repair the Windows partition bootup files manually using the Windows Recovery Console."


Reboot your computer a couple of times and then boot with the 

live cd and try partitioning again. It should work.

I merged it back to my C: disk, so I will shrink again and reboot. I'm glad I know this now.

---

### Post by DanneStrat on 2011-02-12
> **DanneStrat said:**
> I forgot to ask, did you check

the md5 hash of the .iso

you downloaded? It's very important

that your install media isn't corrupted.

Did you check the md5 hash of the .iso?

---

### Post by Ubntu on 2011-02-12
> **DanneStrat said:**
> Did you check the md5 hash of the .iso?

No, I burned it a while ago, so I don't know. The only thing I know, is that it is version 10.10. Btw I'm installing it on a laptop.

EDIT:

Just downloaded it 10.10 again. It's the recent one so hopefully no troubles this time.

Someone lock.

---

