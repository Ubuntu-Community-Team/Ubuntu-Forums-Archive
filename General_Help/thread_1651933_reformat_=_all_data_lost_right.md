---
title: "reformat = all data lost right?"
date: 2010-12-23
forum: General Help
---

### Post by flyingsliverfin on 2010-12-23
I was messing around with grub, syslinux, ubuntu on a usb stick (including dual-booting my usb stick), etc when i somehow managed to change the whole ubuntu hard drive into read-only fs. The next reboot ended in an error something like: ext4 error: filesystem corruption. I can't even enter commands into the prompt it gave me. Next reboot it won't even load grub.

After booting my successfully created ubuntu + UBCD usb stick (that i made before the computer  when crazy) and checking gparted, it says that that the filesystem type for my ubuntu hdd is "unknown". I was wondering that if I try to format it back into ext4, will all my data be lost (or was it lost the first time around)? I'm pretty sure it will be, but i have a faint hope that all my schoolwork/personal projects won't be lost :|

thanks

---

### Post by dcstar on 2010-12-23
> **flyingsliverfin said:**
> 
.........
After booting my successfully created ubuntu + UBCD usb stick (that i made before the computer  when crazy) and checking gparted, it says that that the filesystem type for my ubuntu hdd is "unknown". I was wondering that if I try to format it back into ext4, will all my data be lost (or was it lost the first time around)? I'm pretty sure it will be, but i have a faint hope that all my schoolwork/personal projects won't be lost 

Do a search for rescue tools and various HOWTO recovery posts. You *might* be able to recover some data if you are very lucky.

---

### Post by flyingsliverfin on 2010-12-24
I've looked around, apparently there are some tools to un-format a partition? will that work in my case or should i directly go to look for data recovery tools?

---

### Post by Bitrate on 2010-12-24
Data Recovery tools are you best shot.

Try TestDisk and PhotoRec.  They can be installed via synaptic/apt-get or you can just download a system rescue cd ([http://www.sysresccd.org](http://www.sysresccd.org)) and boot from it.

---

