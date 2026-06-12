---
title: "easier way to transfer files between OS"
date: 2010-03-19
forum: General Help
---

### Post by mefistofeles666 on 2010-03-19
So I've been using ubuntu for quite a while now but I miss having the somewhat internet reliability windows has on laptops. I have been using my wife's laptop for the past 2 months because my internet just completely stopped working on my laptop. I was trying to install opensuse just so I could switch between diff linux distros, but now I'm thinking is better for me to just install windows and the new ubuntu (I'm still using hardy).

here's the problem, I have about 120gb of things in my computer and I just don't have an external harddrive big enough, or the time to be transferring such amount of data just to have it be transferred back. what I wanted to know is if there;s a way to maybe transfer that data after installing both OS. I only have ubuntu, so I can't just go ahead and install windows without having to uninstall hardy.
is there any possible way to partition my drive, transfer all my files there, and then install ubuntu, and windows into two separate partitions and have both OS be able to read from this third partition? does that sound too crazy?

---

### Post by dandnsmith on 2010-03-19
> **mefistofeles666 said:**
> is there any possible way to partition my drive, transfer all my files there, and then install ubuntu, and windows into two separate partitions and have both OS be able to read from this third partition? does that sound too crazy?

No - that's exactly how I have things organised on my PC builds.
It's best if you start from a clean HDD, but you can shrink the space occupied by your single-partition OS to leave spare for the 'data' partition.

You need to pick a partition type understood by all your selected OS - FAT is the simplest, but NTFS can work with NTFS tools in linux (I'm still a bit wary of that, since NTFS is a Msoft owned FStype with which they feel free to change the detail). Both Windows and linux support mounting and use of the added partition.

Note that it's best to do any space squeezing from something outside the OS from which you're currently working.

HTH

---

