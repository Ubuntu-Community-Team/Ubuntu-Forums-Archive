---
title: "[grub2]How to add kernel boot options (e.g. nohz=off) ???"
date: 2009-12-28
forum: General Help
---

### Post by RodGer GR on 2009-12-28
Using grub legacy, adding a kernel boot option was as simple as editing the respective kernel's line in the menu.lst file.

Using grub2, how can I add a kernel boot option?
Thanks in advance for any hint.

---

### Post by sisco311 on 2009-12-28
Edit the /etc/default/grub file and add the kernel parameter to the **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** line, then run:
```
sudo update-grub
```


[uhelp]community/Grub2[/uhelp]
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]

---

### Post by RodGer GR on 2009-12-28
Thanks a lot. Is there a way to add a kernel parameter which will not be default for all the linux systems available but only for those selected.

---

### Post by jimrz on 2010-05-26
@ sisco311 THANK YOU

---

