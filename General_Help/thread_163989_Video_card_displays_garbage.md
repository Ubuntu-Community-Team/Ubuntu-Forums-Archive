---
title: "Video card displays garbage"
date: 2006-04-21
forum: General Help
---

### Post by jblinux on 2006-04-21
I have an AMD 64 system w/ 2GB RAM.  The video card is an eVga Nvidia GeForce 6800 GS CO SE w/ 256MB RAM.  I installed Ubuntu 5.1.  When the computer rebooted, I eventually got a screen of garbage.

I have found the how-to about installing the Nvidia driver, but I can't see anything but colored junk!

How do you get this to boot in text mode?  How are you supposed to download the driver if you can't run Firefox?

It really burns me that I have to use my windoze box to ask for help!

---

### Post by Jason_25 on 2006-04-21
Ctrl-alt-f1, login

```

sudo dpkg-reconfigure xserver-xorg

```
Choose appropriate settings, when you get to the driver section, choose vesa.  Once you exit that, type:
```

sudo /etc/init.d/gdm restart

```

I guarantee this will get you going.

---

### Post by jblinux on 2006-04-22
This worked like a charm.  Much thanks.

---

