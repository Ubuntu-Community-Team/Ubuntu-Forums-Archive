---
title: "touchpad won't work often after boot"
date: 2012-08-19
forum: General Help
---

### Post by hyfanious on 2012-08-19
In my MSI wind u100 netbook
most of the times the touchpad won't recognized after boot, but sometimes it does, and it works fine in Windows Xp
OS: Ubuntu 12.04
tnx in advance

---

### Post by hyfanious on 2012-09-04
I added this line :
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux i8042.reset=1"
```

in this file: /etc/default/grub
and every things works fine now :)

---

### Post by newb85 on 2012-09-04
> **hyfanious said:**
> I added this line :
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux i8042.reset=1"
```in this file: /etc/default/grub
and every things works fine now :)

Please give some details on how you knew to add that line.  Then mark the thread as "Solved".

---

### Post by hyfanious on 2012-09-04
> **newb85 said:**
> Please give some details on how you knew to add that line.  Then mark the thread as "Solved".

U have this parameter by default in that file: 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```u must change it by these values and see which one will help u:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux" 
or GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux i8042.reset=1" 
or GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset" 
or GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux=1" 

```each time use this after changing:
```
 sudo update-grub2 
```and finally do restart.

Hope ur problem will be solved as mine ;)

---

