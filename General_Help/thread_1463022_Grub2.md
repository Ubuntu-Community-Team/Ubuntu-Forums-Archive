---
title: "Grub2"
date: 2010-04-26
forum: General Help
---

### Post by ankit.vader on 2010-04-26
hi.....I have Lenovo Y500 series laptop and I found that when ever I boot system , my keyboard worked some times and some times not .Same thing was happening with my touchpad.

After some googling I found out that it’s neither a problem of Operating System nor a misconfiguration of X11 config file.

It is a problem related to acpi and the 8042 interrupt controller conflicts.

So to get rid of this problem is to edit your grub configuration file ./boot/grub/menu.lst ( on ubuntu) and append the following line to the kernel argument.

locale=fr_FR i8042.reset

```

default=0
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-164.11.1.el5)
root (hd0,5)
kernel /vmlinuz-2.6.18-164.11.1.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet splash
initrd /initrd-2.6.18-164.11.1.el5.imga

```
After the changes, file is.
```

default=0
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title CentOS (2.6.18-164.11.1.el5)
root (hd0,5)
kernel /vmlinuz-2.6.18-164.11.1.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet splash **locale=fr_FR i8042.reset **
initrd /initrd-2.6.18-164.11.1.el5.imga
```
how can i make these changes in grub2?

---

### Post by sisco311 on 2010-04-26
Edit the /etc/default/grub file:
```
...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **locale=fr_FR i8042.reset**"
...
``` 

then run:
```
sudo update-grub
```

[uhelp]community/Grub2[/uhelp]

---

### Post by ankit.vader on 2010-04-26
thx..it worked. Just out of curiosity is it necessary to run update-grub.

---

### Post by sisco311 on 2010-04-26
> **ankit.vader said:**
> thx..it worked. Just out of curiosity is it necessary to run update-grub.

You're welcome!

Yes, update-grub generates the grub2 config file: /boot/grub/grub.cfg, the equivalent of /boot/grub/menu.lst in Grub legacy.

---

