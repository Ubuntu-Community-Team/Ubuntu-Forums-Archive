---
title: "Need help with partitions!"
date: 2012-05-02
forum: General Help
---

### Post by lemro on 2012-05-02
Hi guys,

Im relatively new to ubuntu, and I recently put the upgraded to 12.04 on one of my computers. I had however, forgotten that when In put ubuntu on this computer, I only allocated 4gb of space, just to "check it out". 

Now I have partitioned my drive so I have an additional 100gB of space to utilise, but the new partition just says unallocated.


Edit bodhi.zazen: please use smaller pictures.



How do I allocate this space to ubuntu? (NB: I also run windows 7 on the other partition)

Sorry if this is a common problem, I've been checking the forum, but haven't found anything particular.

Cheers for the help.

---

### Post by oldfred on 2012-05-02
Welcome to the forums.

I see /host, are you now running from Wubi? Little key symbol says it is mounted. Please use screenshots and upload using the little paperclip icon in the edit panel above your message.

You can only use gparted from a liveCD so all partitions are unmounted.

With MBR partitioning  you can only have 4 primary partitions. Primary means Windows can boot from it. One primary can be converted to extended and in the extended you can have essentially unlimited number of logical partitions. 

You already have an extended partition with sda2 with sda5 as a logical using all of it. You can expand the extended left into the unallocated and then create more logicals. 

You have a warning message on sda5, if you click or is right click on it what does gparted say the issue is.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

