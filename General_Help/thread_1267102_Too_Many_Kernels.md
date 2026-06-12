---
title: "Too Many Kernels"
date: 2009-09-15
forum: General Help
---

### Post by Silvernail on 2009-09-15
When I boot I have old kernels showing. I read this site and used the apt-get command as suggest to purge them.

It evidently worked partly. When I boot the list is still there but when I click on one I get a 'non existant' message.

How do I clean up this last part?

TIA 
Dave

---

### Post by muteXe on 2009-09-15
make a back up of /boot/grub/menu.lst, then open menu.lst in a text editor (with sudo/gksudo) and just delete the entries you dont want (actually i'd just comment them out just in case).

mute

---

### Post by Mach1723 on 2009-09-15
open a terminal, and type gksudo gedit /boot/grub/menu.lst and remove 

```
title        Ubuntu 9.04  "OLD KERNEL VERSION HERE"
uuid        8a1bf3a8-176b-47f8-b4fd-39537618e343
kernel       OLDKERNELHERE 
initrd          OLDKERNELHERE
quiet

```

EDIT:just saw that it was answered

---

### Post by TenPlus1 on 2009-09-15
Ubuntu Tweak from getdeb.net gives a nice purge feature for old and un-needed packages/kernels...

---

### Post by esmailgad on 2009-09-15
Did you try the startup manager, in which you can limit the number of kernels at the start up. You can download it from the synaptic

---

### Post by Silvernail on 2009-09-15
Most excellent guys. 
Thanks
Dave

---

