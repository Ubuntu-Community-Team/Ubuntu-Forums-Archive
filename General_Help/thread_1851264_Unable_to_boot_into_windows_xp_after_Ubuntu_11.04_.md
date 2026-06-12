---
title: "Unable to boot into windows xp after Ubuntu 11.04 install?"
date: 2011-09-27
forum: General Help
---

### Post by mojeeq on 2011-09-27
Hey guys, i recently downloaded and installed Ubuntu on my PC, but for some reason, iam unable to boot in windows xp SP3, i can boot into ubuntu and view the files located on the windows xp partition, whenever i want to boot win xp using the grub menu thing, a black screen shows up with a blinking curser on the top left corner...im a bit of a noob, i would really appreciate it if someone helps me out... the boot infor and the hard drive overview is attached...:D

---

### Post by Blasphemist on 2011-09-27
I didn't see the issue except that an unknown boot loader is seen on sda2, don't get that. Try installing boot-repair and using it. If you want, you can first have it create a boot info summary and at the bottom of it you'll see the boot-repair log and that might tell you more. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mojeeq on 2011-09-28
thanks, i will try this...:D

---

### Post by D0natell0 on 2011-09-28
I can personally recommend the boot-repair utility. I've just used to rescue a triple boot system. Admittedly, it took a couple of attempts, but was successful :D
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This link is also very helpful: 
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

