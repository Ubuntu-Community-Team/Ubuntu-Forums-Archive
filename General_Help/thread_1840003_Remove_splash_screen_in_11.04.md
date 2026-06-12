---
title: "Remove splash screen in 11.04"
date: 2011-09-06
forum: General Help
---

### Post by jameshedwards on 2011-09-06
I'm running 11.04 on the Lenovo W520. I don't want a splash screen, i.e. I want to be able to see my grub menu and the boot process. How do I do this ?

james

---

### Post by WorMzy on 2011-09-06
Grub comes before the splash screen. Press and hold shift after POST to see it.

You can still disable the splash screen by removing "splash" from the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub, then running ```
sudo update-grub
```

---

### Post by jameshedwards on 2011-09-06
Thanks ! I had already removed "splash" from grub with no luck in removing the splash screen.

```
james@je-thinkpad:~$ grep -v ^# /etc/default/grub 

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor, nomodeset"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

```

---

### Post by WorMzy on 2011-09-06
Have you updated grub?

```
grep splash /boot/grub/grub.cfg
```

---

### Post by jameshedwards on 2011-09-06
Yes I have updated grub. Thanks ! There is not an inscedence of "splash' in grub.cfg

james

---

### Post by WorMzy on 2011-09-06
Is that a "I've *just* updated grub, and now every thing's working fine", or a "I've already updated grub, and I'm still seeing that damned plymouth screen, raeg!"?

---

### Post by linuxuser12345 on 2011-09-06
Okay, all you need to do is go into the Software Center and uninstall Plymouth Theme packages dealing with the Ubuntu Theme.

I successfully removed my Kubuntu splash screen.

---

