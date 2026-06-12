---
title: "NTFS Resize Issues"
date: 2011-01-31
forum: General Help
---

### Post by Arleas on 2011-01-31
Hi,

I had to use NTFS resize to try and partition a Windows disk with bad sectors.

I successfully resized the partition from 160GB to 100GB.

However, I was unsuccessful in deleting and creating two partitions.

I used the WUBI installer instead, and everything worked great. Why didn't I do this in the first place?!

However, my disk is now saying it's only 90GB. I tried using NTFS resize again, but it's saying that the volume size (160GB, 150GB, anything!) is 'illegal'.

Any help?

PROBLEM SOLVED.

I let my PC boot into Windows. It said the disk was 'dirty' and repaired it. Who would have thought? Used NTFSresize from a gparted LiveCD to successfully resize the partition back to its original size.

---

