---
title: "How to use Menu.lst instead of Grub.conf"
date: 2012-02-20
forum: General Help
---

### Post by rockballad on 2012-02-20
Hello,

After installing XEN, my system generates menu.lst in /boot/grub/ with many kernels to boot. But the grub.conf is not updated regardless that I ran "update-grub" command. And the computer still uses grub.conf to boot (when I remove this file, it can't boot). So, how to make it use menu.lst instead of grub.conf?

Thanks in advance!

---

### Post by jacob.david on 2012-02-20
Usually the menu.lst is a sym link to grub.conf. 
You could try with grub-menulst2cfg. 
grub-menulst2cfg - transform legacy menu.lst into grub.cfg

---

### Post by rockballad on 2012-02-21
Thanks so much for your answer! You helped me solve it!

---

