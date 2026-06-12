---
title: "Auto mount on startup not working"
date: 2009-11-03
forum: General Help
---

### Post by djodjoman on 2009-11-03
In Ubuntu 9.04 and previous releases, if i had a DVD or CD on my DVD/CD-ROM, or a pen-drive or an usb external HD it would be mounted on start-up, and it's icons would be shown on my desktop. Now it is only mounted when i click on nautilus on the left side bar, or if a plug and plug it.

I want the old behavior back. Can anyone help me? I mean, i have a virtual disk on that external hard drive, and i was really used opening virtual box and starting that vm, now i can't, i have to mount the external hard drive somehow before i go do vbox.

Thank you ...

---

### Post by P4man on 2009-11-03
> To control or disable auto mount in Ubuntu 9.10 (Karmic Koala) open a terminal and type gconf-editor followed by the [Enter] key.

Browse to /apps/nautilus/preferences and you will find two keys: media_automount and media_automount_open. 

Rest here:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by djodjoman on 2009-11-03
Both are set to true ...
It 's a bug, it is on startup ... Or a misconfiguration elsewhere

---

### Post by djodjoman on 2009-11-04
I reinstalled ubuntu, and then that bug was way, and i reinstalled many packages ... then the bug was back! I guess there is somepackage messing with something somewhere ... Could it be virtualbox? amarok 1.4?  Or it's dependencies?

Someone please help!

---

### Post by djodjoman on 2009-11-04
It's related to virtualbox libraries or dependencies for sure. I uninstalled, and then I run sudo apt-get autoremove to get rid of its dependencies. Reboot and everything was ok, tried many boots and reboots and things were sweet ... After I reinstall virtuabox and reboot, bang, it wasn't mounting again! This time I even reinstalled virtualbox-ose ...

Does anyone knows the solution for that?

---

