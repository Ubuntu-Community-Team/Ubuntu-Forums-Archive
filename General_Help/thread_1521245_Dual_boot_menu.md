---
title: "Dual boot menu"
date: 2010-06-30
forum: General Help
---

### Post by Selleen rane on 2010-06-30
I dual boot Win 7 and Ubuntu and i was hopping someone could help me edit the GRUB boot screen options as i would prefer it boot into windows not Ubuntu as it is defaulted to.

I have tried these instructions however it seams i do not have a 'menu.lst' file so i can not fallow these instructions
[https://help.ubuntu.com/9.10/switching/dualboot-custom.html](https://help.ubuntu.com/9.10/switching/dualboot-custom.html)

Can someone help me?

---

### Post by eriktheblu on 2010-06-30
Editing menu.lst was the way to customize older versions of Grub. With Grub2, make your changes in /etc/default/grub. Since 9.10, Grub2 has been the default boot loader.

[This thread may help]("This thread may help")

---

### Post by wilee-nilee on 2010-06-30
Using startup manager in synaptic is the easiest way, but I believe it defaults to a line in grub2, so if you upgrade to a new kernel you just have to open startup manager and make sure it's set to W7 still.

You can also change the timeout don't go below 3 seconds though to be safe.

---

### Post by Selleen rane on 2010-06-30
Thank you both very much worked great :D

---

