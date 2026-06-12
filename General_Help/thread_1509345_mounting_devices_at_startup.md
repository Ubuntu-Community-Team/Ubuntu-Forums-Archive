---
title: "mounting devices at startup"
date: 2010-06-14
forum: General Help
---

### Post by fx69 on 2010-06-14
Hi,
I'm getting all devices mounted at startup while I don't need them though.
How to disable this ? :)

---

### Post by dino99 on 2010-06-14
into synaptic you can install mountmanager to deal with all the partitions and devices rights, then set your preferences into: system admin mountmanager

---

### Post by dapperdanny77 on 2010-06-14
/etc/fstab:

add noauto option to the options in the 4th column - options are comma separated.

you can find detailed information in the manpage

man fstab

---

### Post by fx69 on 2010-06-14
Thank you both :) Devices are not mounted anymore, but I have another question:
When I manually mount a device an icon appears on desktop. I've read somewhere that this option can be turned off by changing value of "apps->nautilus->preferences->show_desktop" to 'false' in gconf-editor. I remember it used to work on another machine but on this one I still see those icons on desktop even the value isn't set :/ Do you know why's that ?

---

