---
title: "Ubuntu 10.4 and RAID"
date: 2010-09-04
forum: General Help
---

### Post by cinohpa on 2010-09-04
So I have raid on my gigabyte ud4p in ubuntu 10.4. I created a raid 5 array with 3 disks.

The array is recognized in windows and I was able to format it. 

In 10.4, it sees all the disks, and it says 2 of the disks are RAID components and that the 3rd disk is unknown (maybe this is the parity disk and ubuntu thinks of it differently?) It doesn't seem to see the partion that I put the 3 disks into.

Seeing as it understands that there is a raid array floating around, I am wondering if there is just a little more I have to do to something to make things work.

Thanks.

SOLVED: yay. Works now. Followed the steps here about installing dmraid. This command: sudo modprobe dm-raid4-5 didn't work, but my array still got mounted properly.

---

