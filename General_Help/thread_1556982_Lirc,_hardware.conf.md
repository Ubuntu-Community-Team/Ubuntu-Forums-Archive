---
title: "Lirc, hardware.conf"
date: 2010-08-20
forum: General Help
---

### Post by gobba on 2010-08-20
Hi!
Ive installed lirc, and the remote is mapped to /dev/lirc0 and if i change in hardware.conf to use /dev/lirc0 it works fine. But everytime i reboot it changes the hardware.conf to /dev/input/event7 instead!

How do i stop it from changing hardware.conf at every reboot? Or even better. How do i get it to autoconfigure my remote to get /dev/input/eventx link which will be chosen in hardware.conf?

cheers
-gob

---

### Post by gobba on 2010-08-20
I Found it. It was a the tv-card that had its own remote and it installed a script in /etc/udev/rules.d that rewrote the hardware.conf file.

This was for a sundtech device in case someone else gets troubled by this. =)

cheers
-gob

This thread should be tagged solved, but dont know how to do it.

---

