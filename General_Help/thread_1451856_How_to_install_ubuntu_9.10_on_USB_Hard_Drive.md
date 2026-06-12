---
title: "How to install ubuntu 9.10 on USB Hard Drive"
date: 2010-04-11
forum: General Help
---

### Post by jadmaestro on 2010-04-11
Hello all,

I'm a total noob about ubuntu. I am currently using XP and I would like to try ubuntu 9.10. I already tried ubuntu 9.10 using virtualbox and Im impressed by the look and performance. However, I still need more time before I fully install ubuntu in my notebook.

I'm aware that linux's distro is possible to be installed and boot from USB. Most tutorials that I google provide step by step on how to install linux distro (fedora,ubuntu,mint) to USB stick and flash. The dilemma is that I don't have USB stick instead I only have 320gb USB hard drive. And I tried to install ubuntu 9.10 using unetbooting to my USB hard drive but my hard drive is not listed in the USB drive box option.

For information, I created two partition in my USB hard drive, 150gb each. Is it possible to install ubuntu 9.10 on partition 2 and boot the OS from there? 

Please help me with tutorials on how to install ubuntu 9.10 to a USB hard drive (second partition). 

Links and replies are highly appreciated....

---

### Post by cj.surrusco on 2010-05-16
This may help 
[http://ubuntuforums.org/showthread.php?t=1478020](http://ubuntuforums.org/showthread.php?t=1478020)

---

### Post by maestrobwh1 on 2010-05-16
You might also want to create a 4.75 GB fat32 partition and use the USB startup disk creator and make a 4 GB persistence file.  Limit is that no file than 4 GB can exist on fat32.

You could also make another file system and use unetbootin and you can make the persistence file even bigger on ext 3/4.

---

### Post by C.S.Cameron on 2010-05-16
With 150 GB of space I would suggest unplugging your internal HDD and doing a full install to your USB drive as suggested in the link above.
With a persistent install, (usb-creator, UNetboootin, it is hard to upgrade the system and without separate casper-rw or home-rw partitions you are limited to 4GB of persistence space.

---

