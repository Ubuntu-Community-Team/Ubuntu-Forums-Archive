---
title: "Partimage help"
date: 2009-08-07
forum: General Help
---

### Post by emeraldgirl08 on 2009-08-07
I want to make an backup of an NTFS partition using Partimage. I've gone to the Partimage website and read some related threads here. I've even booted into Partimage (via System Recovery liveCD) and found it difficult to use for first-timers!

I have an internal HD that has an exact NTFS partition I'd copied and pasted with Gparted. It's taking up 13.7 Gb and includes a separate but needed system-restore partition of 1.6 Gb. I've made that a hidden partition and shoved it to the back of the HD. I've decided after hearing about it to make a zipped up image of both partitions and store them on DVD.

Whenever I go into the GUI of System Recovery I don't know where to begin. I choose Partimage and when I select the partition I want to image I don't know how to mount my external DVD drive.

Is it something like:    mkdir /mount/dvd ????

I'm not so sure b/c I don't know if the DVD drive has a specific drive letter name! Do I just call it DVD???

My setup consists of using my lappy DVD drive for running the Partimage LiveCD. There is the internal HDD that has the partitions I want. There is also the external DVDRAM writer that I want to burn the partitions to.

Any advice??? 

TIA!

---

### Post by emeraldgirl08 on 2009-08-08
Just got in from work! 

Hmmm... no one has got an idea? I've read up on this but still am unclear about mounting the ext. DVDRAM to write to.

---

### Post by ju2wheels on 2009-08-08
Ive never used the Partimage live cd but /dev/scd0 should be your DVD device path.

---

