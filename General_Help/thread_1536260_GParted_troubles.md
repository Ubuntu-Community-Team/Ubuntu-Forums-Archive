---
title: "GParted troubles"
date: 2010-07-21
forum: General Help
---

### Post by PhoenixGraphix on 2010-07-21
I bought a computer from Best Buy, and this was after the 7 rush to upgrade, so a 15 GiB Vista boot partition was left on my computer's hard drive. I deleted it with GParted, and (since it was on the far left) began moving the remainder of the partitions to fill up that space. I had an intractable Windows 7 Partition that absolutely refused to shrink itself beyond 400 GiB (Yeah, ridiculous right? That's why I switched to Ubuntu). So, I began moving this partition, which (I was informed) would take around 4 hours. So, I went to bed and decided to check up on it the next morning. I had already had Ubuntu installed, and was running it from the installed version. When I checked up on it, the screen had locked and I could not wake it. So I did what seemed obvious to me. It was already far past the point when GParted should have finished, so I assumed that it was safe (Yes, I tried literally every key and key combination on the keyboard). So I pressed and held the power button until my machine shut down, and started it up again. I booted into Ubuntu, and fired up GParted to check on my partition. It was corrupt. I assume that my machine locked up before GParted could finish moving all of the data. So now I have one 15 GiB larger partition that has "corrupt data" on it. I know that of the 400 or so GiB that the partition occupied, I used no more than 60 of it, and I am sure that at least 60 GiB of data was successfully moved with GParted before I went to bed. So, is there a way for me to recover this data, do I need a recovery disk, or is it lost forever?

Help is GREATLY appreciated, and thanks for any suggestions in advance.

---

### Post by watupgroupie on 2010-07-21
Try running [TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

