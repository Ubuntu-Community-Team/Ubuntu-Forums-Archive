---
title: "Ubuntu Partition Question"
date: 2010-04-14
forum: General Help
---

### Post by DedMoroz on 2010-04-14
Hi Hi. Got a question while gparted is doing its thing right now.

Ive got a 500gb hard drive.

-sda1 is 400gb (ubuntu 9.10/32bit/ext3)
-sda2 is 50gb (ubuntu 10.04/64bit/ext4)

Id like to expand my lucid partition now and eventually get rid of my 9.10 partition. Ive got an 80GB virtualbox file sitting on sda1 that i need and want to expand sda2 now so i can first copy the VB file over, then expand sda2 completely.

I need help :) I just finished creating sda3 ext4, but cant figure out how to merge it with sda2 (well really sda6). Please see image. Thanks for any help!!

[http://imagebin.org/93016](http://imagebin.org/93016)

---

### Post by DedMoroz on 2010-04-14
As u can see in the photo, there are lock symbols (i was running off of a livecd too) so i figured that was a prob. I decided to use terminal and go into gparted as root, see if that would help and it did not help.

I did solve my main issue by using parted magic disc on one of those rescue CDs like "super rescue disc".. i forget what flavor rescue disc im using offhand and im not going to take the disc out now :) anyhow, Im in gparted from that rescue disc and i did not see those lock symbols as I did in the liveCD of Ubuntu 9.10. I 'm now able to remove the sda3 i made, then expand my sda2/sda6 i wanted to expand.

---

