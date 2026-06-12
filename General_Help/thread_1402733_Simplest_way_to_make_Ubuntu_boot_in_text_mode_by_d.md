---
title: "Simplest way to make Ubuntu boot in text mode by default"
date: 2010-02-09
forum: General Help
---

### Post by krige on 2010-02-09
Hi there,

what is the simplest way to make Ubuntu boot in text mode by default?

I can't uninstall gdm because occasionally I want to be able to switch in graphical mode by running startx.

I tried the command:

```
# update-rc.d -f gdm remove
```

as suggest by [this page]("http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html/") but didn't work.

I can't edit inittab because Ubuntu has abandoned in favour of upstart. In the upstart README is said in order to change the runlevel you need to edit /etc/init/rc-sysinit.conf and change the DEFAULT_RUNLEVEL variable, which by default is set to 2. The problem is I don't know to what value I should set it to. Ubuntu/Debian apparently have incomprehensible ideas about runlevels: runlevels 2-5 are the same, all of them start the GUI.

I personally find quite bizzare such a simple need is not well documented and I am surprised there isn't a plain option like "Run in graphical mode by default?" YES/NO.

---

### Post by krige on 2010-02-09
I have found the solution on [this post]("http://www.hipergalaxia.org/blog/2010/01/05/iniciar-linux-ubuntu-9-10-en-modo-solo-texto/"), it works!!!

You simply need to open the /etc/default/grub file, locate the following line:

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8220;
```

and change it to:

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash [COLOR="Red"]text[/COLOR]&#8220;
```

and don't forget to run 'update-grub' afterwards to update.

---

