---
title: "Power Loss while expanding NTFS partition"
date: 2011-07-28
forum: General Help
---

### Post by cgeorge1122 on 2011-07-28
Hi wonderful experts.

I was recently expanding my 1.4 TB NTFS filesystem, when I lost power to my system. It is currently recognized as HPFS/NTFS (0x07) partition type by the 11.04 Disk Utility.

I'm not sure if I'm going about this correctly, but in following the guide [here]("https://help.ubuntu.com/community/DataRecovery#Software%20choices") I am using ddrescue from a live CD to make an image of the partition. It has currently rescued approx. 70 MB of data, so it still has a while before it is complete.

Just wondering if anyone has any advice for such a situation. This is my first foray into data recovery and I'm rather nervous since this disk has EVERYTHING on it.

Thanks,
cgeorge1122

P.S.
Any advice except for buying a UPS and backing up frequently. I should already be doing that #-o...

---

### Post by Steam. on 2011-07-28
Anything APC/Liebert is usually good, i have a 2200VA liebert, it holds around longer than you need to save docs and stuff.

---

### Post by Mark Phelps on 2011-07-28
> **cgeorge1122 said:**
> Just wondering if anyone has any advice for such a situation. This is my first foray into data recovery and I'm rather nervous since this disk has EVERYTHING on it.

My own experience is that MS Windows utilities are better at recovering NTFS filesystem problems than Linux utilities; and vice versa.

If you're not able to recover all your files and folders, I heartily recommend you do the following:
1) Go to the runtime software site, download and install GetDataBack for NTFS on a working MS Windows PC
2) Connect the damaged drive to the working PC
3) Run GetDataBack in the deepest discovery mode -- with a partition this big, it will need to run overnight.  See what it finds.
4) If it finds what you need, go to Runtime Software, purchase the product, download and install the serial key.  Then, use the product to recovery your files and folders.

Your stuff -- your money.

---

