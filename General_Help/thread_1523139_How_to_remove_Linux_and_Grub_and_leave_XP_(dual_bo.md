---
title: "How to remove Linux and Grub and leave XP (dual boot)"
date: 2010-07-03
forum: General Help
---

### Post by tom1g on 2010-07-03
Hi.

I recently installed Kubuntu and need to get it out now. What is the easiest way to do that? I also have an installation of WinXP and would like to boot it afterwards :)

Please help me, it's quite urgent

---

### Post by philinux on 2010-07-03
First off backup anything important just in case murphy's law.

If you have installed grub to the mbr then you need to restore the windows XP bootloader to the mbr.

Section #16 first link [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Once you have windows booting normally you can delete the kubuntu partition.

---

### Post by tom1g on 2010-07-04
That sounds reasonable, thanks. Actually, I have to do this process on ~5 computers, and one of them has both working bootloader and GRUB. First bootloader loads and offer two options: XP and Kubuntu. After choosing Kubuntu, GRUB is loaded. Should I do something different in this case?

---

### Post by dino99 on 2010-07-04
grub2 (grub-pc) or grub1 (legacy) ?

sudo update-grub

---

### Post by tom1g on 2010-07-04
Grub2. I also used update-grub and output was normal. Now I'm facing Error 15 when I try to boot from GRUB.

---

### Post by dino99 on 2010-07-04
is it a fresh install or an dist-upgrade with grub1 previously installed ( in case, you need to remove menu.lst and run again: sudo grub-mkconfig && sudo update-grub)
( only grub-pc and grub-common installed on your ubuntu partition)

---

### Post by oldfred on 2010-07-04
When you said 
First bootloader loads and offer two options: XP and Kubuntu.
Was this a wubi install where windows boots and the boot.ini also has a selection for Ubuntu.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

