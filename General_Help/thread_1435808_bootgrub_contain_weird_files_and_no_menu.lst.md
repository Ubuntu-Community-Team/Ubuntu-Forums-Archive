---
title: "boot/grub contain weird files and no menu.lst"
date: 2010-03-21
forum: General Help
---

### Post by MuffinMan123 on 2010-03-21
All I see are .mod files and .img files and 2 .lst files, but I didn't find any menu.lst, shouldn't this file be here by default?

how does xubuntu boot to this default partition? what was the setting?
also, how do I set up multiboot with different distros? all I need to do is the edit the /boot/grub/menu.lst right and add the partition with the /root for that distro right?

---

### Post by asmoore82 on 2010-03-21
I believe starting with Ubuntu 9.10 Karmic, it has switched to GNU Grub version 2.

menu.lst is now grub.cfg and _***cannot***_ be edited directly -
see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

In a nutshell you edit "/etc/default/grub" and files in "/etc/grub.d/" and run
```
sudo update-grub2
```

---

