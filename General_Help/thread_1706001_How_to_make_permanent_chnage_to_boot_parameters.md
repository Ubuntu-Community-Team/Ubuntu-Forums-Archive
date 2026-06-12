---
title: "How to make permanent chnage to boot parameters"
date: 2011-03-13
forum: General Help
---

### Post by XEtedBear on 2011-03-13
To solve some obscure hardware issues on my system I need to boot the kernel to use HPET timers. It is straightforward to edit the necessary additional options into the Grub2 boot menu at boot - but this becomes tedious.

I looked at ways of adding these additional options permanently in some config files, as described in the Grub2 editing guide. Aside from the fact that its most important parts are written in Geek (and is therefore well over the horizon from my ability to comprehend), it seems to imply that I cannot modify existing lines in the boot menu, only add new lines. I wouldn't know how to specify the additional options I want in a new line.

I tried using StartUpManager. It fails on my system with:

```

GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.1/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)

```

Is there a technique which will allow me to add options  'hpet=force' and 'clocksource=hpet' to my default kernel boot menu entry?

---

### Post by dnairb on 2011-03-13
In terminal:

```
gksudo gedit /etc/default/grub
```

This will open a file in which there are various user-configurable settings.

Line 9 (IIRC):

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

change to what you require, for example in your case:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force clocksource=hpet"
```

Save the file, then in terminal update grub:

```
sudo update-grub
```

then reboot

---

### Post by XEtedBear on 2011-03-13
I must say that that procedure was clearly enough explained and painless enough to execute and it actually worked too!.

Thank you very much. I can't see any reason why the bulk of the Grub How To couldn't have been written with similar clarity.

---

