---
title: "Keyboard Issue"
date: 2011-02-08
forum: General Help
---

### Post by Erroler on 2011-02-08
Hey There! I'm new to linux. I bought a VPS of 123systems.net
I installed linux Ubuntun 10.10 on it. I followed [this guide]("http://wiki.ubiquityservers.com/index.php/How_to_install_VNC_on_Ubuntu") and installed Gnome and TighttVnc Server on it. The problem is when I connect to my VPS using VNC, the keyboard gets all messy. when I type minecraft it gets like %6gj&9[! , I cant use backspace, I use 5 instead. I tried to reinstall it 4 times. And rebooted my computer twice and tried to connect trough Real Vnc to it, but without any luck! Staff tried to connect to it trough VNC and had the same problem.

:)

---

### Post by Erroler on 2011-02-09
Still need help guys :(

---

### Post by P4man on 2011-02-09
Google suggests you run this on the server:
```

gconftool --set /desktop/gnome/peripherals/keyboard/kbd/layouts --type List --list-type String [aa]
```

or this

```
Add the following line to /etc/gdm/Xsession:

    export XKL_XMODMAP_DISABLE=1
```
sources:
[http://pietercvdmlinux.blogspot.com/2010/07/running-tightvncserver-on-ubuntu-1004.html](http://pietercvdmlinux.blogspot.com/2010/07/running-tightvncserver-on-ubuntu-1004.html)
[http://dertompson.com/2010/02/09/tightvnc-messes-up-keyboard-layout-after-ubuntu-upgrade/](http://dertompson.com/2010/02/09/tightvnc-messes-up-keyboard-layout-after-ubuntu-upgrade/)

---

### Post by Erroler on 2011-02-09
Thank you so much!!! The first method worked fine for me!!!!
THX :guitar:

---

