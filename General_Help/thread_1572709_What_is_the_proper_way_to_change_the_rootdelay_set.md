---
title: "What is the proper way to change the rootdelay setting in Ubuntu?"
date: 2010-09-11
forum: General Help
---

### Post by CyanLights on 2010-09-11
Hi everyone,

I just installed the latest version of the Ubuntu desktop edition via the live CD on an extra computer as the only operating system. When I boot to Ubuntu, BusyBox appears and I've come to the conclusion that, like many others, the root delay setting needs to be longer for it to detect Ubuntu. In order to actually boot. I have to type "exit" into busybox.

I've gotten that far, but I didn't want to go around changing system files (to my understanding, that system file would be /boot/grub/grub.cfg) without knowing exactly what I was changing. So, all I'm really asking is for someone to lay it out step by step, because I'm not entirely sure where to put the rootdelay=# in that file (if thats the file that needs to be changed)

If you need me to post the contents of that file or any system specifications, I would be happy to do so. Thank you so much.

---

### Post by dcstar on 2010-09-11
> **CyanLights said:**
> Hi everyone,

I just installed the latest version of the Ubuntu desktop edition via the live CD on an extra computer as the only operating system. When I boot to Ubuntu, BusyBox appears and I've come to the conclusion that, like many others, the root delay setting needs to be longer for it to detect Ubuntu. In order to actually boot. I have to type "exit" into busybox.

I've gotten that far, but I didn't want to go around changing system files (to my understanding, that system file would be /boot/grub/grub.cfg) without knowing exactly what I was changing. So, all I'm really asking is for someone to lay it out step by step, because I'm not entirely sure where to put the rootdelay=# in that file (if thats the file that needs to be changed)

If you need me to post the contents of that file or any system specifications, I would be happy to do so. Thank you so much.

Do **not** touch those generated files. Search out the many Grub2 HOWTOs on where to make the appropriate changes and what to do afterwards.

Start with /etc/default/grub.

---

