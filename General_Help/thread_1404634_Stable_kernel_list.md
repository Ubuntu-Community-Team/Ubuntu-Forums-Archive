---
title: "Stable kernel list"
date: 2010-02-11
forum: General Help
---

### Post by sr_guy on 2010-02-11
Currently, I am running Intrepid. I run it as a media center (mythtv) and as a PBX (Asterisk + FreePBX). I also have a completed Jaunty install ISO'd with the same setup. But I am having issues with both distros with kernel versions of v2.6.28 and above. Issues like Asterisk trunks freezing after bootup, Nvidia driver issues, and Lirc problems. Version 2.6.14 works just fine with everything. 2.6.15 everything works except Lirc. It won't boot at all with 2.6.16 and 2.6.18. Luckily I've backed up menu.1st so I can just boot up using an older kernel and edit menu.1st. I still would like to update to a kernel that works with everything since I have noticed system performance improvement with newer kernels. If anyone has kernel suggestions for both Intrepid & Jaunty that might work with my setup, I'm all ears.

I did find this list, by the way.

[http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html)

---

### Post by sr_guy on 2010-02-15
This post help me and I've locked my kernel at 2.26.17 on Jaunty by editing /boot/grub/menu.lst

[http://newyork.ubuntuforums.org/showthread.php?t=839215](http://newyork.ubuntuforums.org/showthread.php?t=839215)

Asterisk, Mythtv, Mythstream and Nvidia are all stable now. :p

---

