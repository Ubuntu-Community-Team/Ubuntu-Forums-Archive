---
title: "A 64 bit equivalent of DBAN for disk wiping?"
date: 2010-05-19
forum: General Help
---

### Post by BastardNamban on 2010-05-19
I convinced my younger brother to convert to Ubuntu after his computer became crippled by viri.

I've backed up his files, and I want to wipe his HDD. I've used the wonderful Darik's Boot & Nuke utility for years now, but the computer I'm trying to wipe is 64 bit- DBAN will only work on 32 bit stuff.

Can anyone recommend something I can burn to CD and wipe the drive as well as DBAN? I was thinking of just using GParted from the 64 bit live CD to delete the windows partition if I can't find anything.

Sugguestions?

---

### Post by jbrown96 on 2010-05-19
Any Linux liveCD ```
sudo dd if=/dev/urandom of=/dev/sda
``` Assuming that sda is the drive you want to erase.

Almost every Linux liveCD contains shred as well. The only difference that it will give you some output and can be run multiple times. ```
sudo shred -n # -vv /dev/sda
``` where # is the number of passes

---

### Post by -humanaut- on 2010-05-19
You could use any LiveCD open a terminal you can use fdisk,cfdisk or Gparted.

Or you could just use Ubiquity (the Ubuntu installer) to partition the drives as well. It's not really necessary to "Boot & Nuke" to install Ubuntu or any Linux for that matter over Windows.

---

### Post by pirateghost on 2010-05-19
i fail to see how DBAN wont run on a 64bit CAPABLE system.  64bit hardware is perfectly fine running 32bit software

---

### Post by BastardNamban on 2010-05-19
Thanks for the quick replies. I did not know about shred.

I'm typing from my laptop in which I did use Gparted to erase windows partitions not big enough and installed ubuntu at the end- I haven't been having any problems so far.

I guess I will just use Gparted again. Thanks- I'll have to try shred next time I do this.

---

