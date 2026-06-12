---
title: "understanding /dev"
date: 2011-06-24
forum: General Help
---

### Post by raj17 on 2011-06-24
Hi,
Could some one explain me about /dev in linux. when I enter ls /dev all devices  r coming on my  system i dont know what is what. have  some idea on sda and hda but not others come explain me what tty#,ttys#, loop, ram etc are. i've browsed for it but i'm not able to find clear answer. most of them r explain about sda and hda but not others. i've attaced nothing to my system. i dont know where from it is finding so many devices.
thanks,
raj

---

### Post by fdrake on 2011-06-24
> **raj17 said:**
> Hi,
Could some one explain me about /dev in linux. when I enter ls /dev all devices  r coming on my  system i dont know what is what. have  some idea on sda and hda but not others come explain me what tty#,ttys#, loop, ram etc are. i've browsed for it but i'm not able to find clear answer. most of them r explain about sda and hda but not others. i've attaced nothing to my system. i dont know where from it is finding so many devices.
thanks,
raj

in linux everything is a file. therefore your devices and your hardware are represented as files. Ram, tty (screens), cdrom etc are of files that controls your devices. it's not very easy to explain but if you read about the linux kernel and how it work you can have a general idea of it.

help link [http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/]("http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/")

---

### Post by raj17 on 2011-06-24
thank u

---

### Post by 3rdalbum on 2011-06-24
/dev also has a lot of files that are virtual devices, not real physical hardware. For instance, you mentioned "loop" - now there's no physical loop inside your computer, but the "loop" device is what makes it so easy to mount a disk image and have it treated exactly the same as the physical disk.

---

