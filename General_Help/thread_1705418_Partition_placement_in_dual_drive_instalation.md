---
title: "Partition placement in dual drive instalation"
date: 2011-03-12
forum: General Help
---

### Post by f3nr1c on 2011-03-12
Hello all, 
            I am about to install Ubuntu on a system which has two internal hard drives, and I am rather indecisive about the placement of the /tmp and swap partitions. 

The intention is to place the root partition on sda, and /home on sdb. Is there any particular placement for the /tmp and swap which would be particularly beneficial, i.e. from the perspective of performance gains/ read/write speeds (or any other advantages I may not have taken into consideration)? Or would it not really make a difference?

Any advice would be welcome. 

My thanks in advance. 

F3nr1c. :D

---

### Post by Joe of loath on 2011-03-12
Personally I'd keep /tmp as part of /, and put the swap on the fastest drive.

---

### Post by JRV on 2011-03-12
I put /tmp on ramdisk by adding the following line to /etc/fstab:
```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

Firefox puts its cache in your home partition. By moving this cache in RAM you can speed up Firefox and reduce disk writes. 
Mount /tmp in RAM, and you can put the cache there as well.

Open about:config in Firefox. Right click in an open area and create a new string value 
called "browser.cache.disk.parent_directory". Set the value to /tmp.

And I would put /home and swap on the fastest drive.

---

### Post by vanadium on 2011-03-12
> **f3nr1c said:**
> Hello all, 
Or would it not really make a difference?


swap: It would not really make difference, in fact. As soon as Ubuntu needs swap, the system becomes very slow anyway, and putting it on the "fastest" drive won't feel much different.

tmp: Indeed keep it simple and just keep with with the root partition. Putting these things in memory may be beneficial if you really have plenty of ram. Else, I would guess you better give a maximum of ram to the system, and use fysical drives for any tmp space.

---

### Post by f3nr1c on 2011-03-12
> **JRV said:**
> I put /tmp on ramdisk by adding the following line to /etc/fstab:
```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```Firefox puts its cache in your home partition. By moving this cache in RAM you can speed up Firefox and reduce disk writes. 
Mount /tmp in RAM, and you can put the cache there as well.

Open about:config in Firefox. Right click in an open area and create a new string value 
called "browser.cache.disk.parent_directory". Set the value to /tmp.

And I would put /home and swap on the fastest drive.


That's a fantastic idea! I have ram to spare, and I should think I'd see some significant improvements with a lot of tasks. Great suggestion. Thanks. I will give that a go.

---

### Post by lithopsian on 2011-03-12
Putting browser cache in RAM, except for very advanced forms that are written out to disk later, is counter-productive.  The cached data that Firefox feels will be needed again in the current session is kept in RAM anyway.  The rest is cached so that when you reload that page in a week or a month the data will be on your machine already, except you put it in RAM and then blew it away when you rebooted. If you have so much RAM that you feel like having a tmpfs then there are better uses for it.  You should also consider just increasing the size of your compcache and everybody will benefit.

I also don't suggest putting /tmp on a separate partition unless you have rather unusual needs.  Having a partition that is always empty seems rather pointless.

Placement of swap is not important on most desktop machines.  I keep recommending people stick it in a file and then it can be moved or resized to anywhere and anything you like.  Whichever way you go, placement shouldn't matter much unless you are doing something truly weird.

/ and /home on separate drivers might help, but also consider whether they are on separate controllers and maybe you won't see all the potential benefits.

A separate data area for the sort of things people clutter their drives with these days: videos, photos, music, etc.  Nice for it to be persistent when you have to reinstall.  You could say that is what /home is for, but sometimes you could need to replace /home too.  Also, some multiple Linux installations won't be able to share /home but they can share a data partition and you'd almost certainly want them to.

 There are things you might want to partition, but usually you won't.   Things like /var, /opt, even /lib or /usr/lib but generally it is more trouble than it's worth for a desktop system.

---

