---
title: "Removing a distro from a dual boot system"
date: 2012-06-08
forum: General Help
---

### Post by craig10x on 2012-06-08
Here is my current set-up...i am dual booting with ubuntu 12.04 and Zorin 6 RC...
Now, if i wanted to just remove the Zorin 6 RC, and resize so that ubuntu takes the full drive space again, and remove the dual boot up that i get when i first boot my computer, how would i go about doing that?

I have never done it before...is there some basic, simple way to do that?

By the way, both were installed using the ubuntu type of installer...ubuntu was the first to be installed by itself and then Zorin was later added (i selected the automatic option of installing "side by side"....

Partition wise, it is set up as just 2 partitions (1 for ubuntu and 1 for zorin) and a 1 swap file for both systems...

---

### Post by Enigmapond on 2012-06-08
Easiest way is to boot a liveCD of Ubuntu then use gparted to change the partitions to what you desire. Or you can boot into your Ubuntu and do the same thing however you would not be able to adjust the current ubuntu partition as it needs to be un-mounted.

---

### Post by mike555 on 2012-06-08
Be sure to update-grub.

---

