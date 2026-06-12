---
title: "Error no such device ( lots of numbers ) Grub Rescue&gt;"
date: 2010-08-10
forum: General Help
---

### Post by sumant_neo on 2010-08-10
Hi! I'm a total noob at linux ubuntu and just wanted to try it out. So, I downloaded wubi to install it on my old desktop which runs windows xp pro. The installation went through and it asked for some updates. After the updates, it rebooted but got stuck to the msg in the topic sentence. I don't have no live cd's for ubuntu and tried to read some earlier threads but they don't make any sense to me as I have no previous knowledge of linux. Can someone please explain on how to deal with this in a simpler language? PLZ! Thanks!

---

### Post by bcbc on 2010-08-10
> **sumant_neo said:**
> Hi! I'm a total noob at linux ubuntu and just wanted to try it out. So, I downloaded wubi to install it on my old desktop which runs windows xp pro. The installation went through and it asked for some updates. After the updates, it rebooted but got stuck to the msg in the topic sentence. I don't have no live cd's for ubuntu and tried to read some earlier threads but they don't make any sense to me as I have no previous knowledge of linux. Can someone please explain on how to deal with this in a simpler language? PLZ! Thanks!

You need to get the windows bootloader back in place in the disk MBR (master boot record). It was replaced by the grub bootloader when you were running updates: there was a screen that asked where to install grub, and you probably selected /dev/sda (your hard drive).

So, if you don't have a live CD you will need your windows disks or a windows repair CD. Then you can replace the bootloader as described here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) (scroll down to the XP instructions)

---

### Post by sumant_neo on 2010-08-15
Thanks a lot!! Saved my PC! I used the windows repair disk.

---

