---
title: "Wubi hibernating on Flash card?"
date: 2012-02-12
forum: General Help
---

### Post by dieter-erich on 2012-02-12
Hi,
 I have been happily using wubi since quite a time running on an eeePC 1005HA. However, I am missing hibernation that is most useful for a quick start. I already have 4 primarIy partitions on the HD and so I cannot make any new one to be used for swap. 

Is it possible to use a flash card (e.g. with 2GB) to as storage for the hibernation files? If so, how would I have to set it up? Would I need to delete the loop-mounted swap for wubi to only use the flash card (formatted as the unique swap partition, I guess) or could I dedicate the flash card to hibernation only?

Thanks for hints, D-E

---

### Post by bcbc on 2012-02-12
The swap partition needs to be > the size of your RAM. So it would likely work provided you have less than 2GB ram. [http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html](http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html)

Also, you'll need the USB plugged in when you boot wubi. It's certainly less convenient than having it on your internal drive. When I did it, I removed the wubi swap - since it was pointless having a 255MB swap in addition to 4+ GB of swap to cover my RAM, neither of which were used much.

---

### Post by dieter-erich on 2012-02-14
Thanks for the hints! The size would not matter, I could easily get a bigger card. But, I suppose that I run into troubles when removing or replacing the flash card since it has to be permanently registered in fstab. So, definitely a not so good idea!

---

