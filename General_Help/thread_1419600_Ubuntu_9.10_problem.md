---
title: "Ubuntu 9.10 problem"
date: 2010-03-02
forum: General Help
---

### Post by Rakic on 2010-03-02
Instaled ubuntu 9.10 and i like it more than win xp because you can setup it in your way.

Now my problem is when i compile older kernel with my setup and restart ubuntu i get grub with no loads like config is gone or something so i cant boot any of default kernels.
I folowed this guide for compile [http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization](http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization)
because i want to create lan hlds server with 1000hz kernel and have best response and latency server.

can anyone confirm is this guide working with this 9.10 version or problem is that i cant set older kernel with newest ubuntu?

Compiled few times and annoyed to wait again 2h just to try some other explanations i found on internet.

Im new to ubuntu but i wanna learn about it.

thx

---

### Post by darolu on 2010-03-02
It looks like the GRUB is messed up to me.
That guide's GRUB changes refers to GRUB (legacy), not GRUB2; Ubuntu 9.10 installs GRUB2, so that might be why it is failing.
Follow this guide to fix it, once you run update-grub your new kernel should be added: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

