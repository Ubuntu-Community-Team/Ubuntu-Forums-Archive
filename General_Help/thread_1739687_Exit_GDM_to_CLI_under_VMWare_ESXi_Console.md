---
title: "Exit GDM to CLI under VMWare ESXi Console ?"
date: 2011-04-26
forum: General Help
---

### Post by m1k30rz on 2011-04-26
Hi there,

I am learning to run VMWare ESXi and have installed Ubuntu 10.10 in a virtual machine.

People say you press CRTL+ALT+F1 to exit back to command line from the gnome login screen but this never works for me.

If I do something like "sudo service gdm stop" it just delivers me to the desktop background almost like the machine has hung, no menus toolbars, mouse or anything.

Basically what I want to be able to do is start up the machine with command line, and go into gnome on occasion and exit back out to command line to save resources, this is because the machine will mainly serve as a web server.

I followed the guide here [http://www.thecoderanger.com/disable-gdm-at-system-boot-ubuntu-10-10-maverick/](http://www.thecoderanger.com/disable-gdm-at-system-boot-ubuntu-10-10-maverick/) which tells how to make ubuntu always start at CLI, which works nicely, but I need a way to be able to get back to CLI from inside gnome.

Thanks :)

---

### Post by m1k30rz on 2011-04-26
Anybody?

---

### Post by m1k30rz on 2011-04-28
Hmm?

---

### Post by chenxiaolong on 2011-04-28
Try:

```
sudo /etc/init.d/gdm stop
```

If that doesn't work, try switching to runlevel 3

```
sudo init 3
```

---

