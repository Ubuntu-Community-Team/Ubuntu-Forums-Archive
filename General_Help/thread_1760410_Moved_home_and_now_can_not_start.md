---
title: "Moved /home and now can not start"
date: 2011-05-16
forum: General Help
---

### Post by newairly on 2011-05-16
ubuntu 10.04 Easy Peasy  eeepc 900

I have messed up my home directory and can not get out of the mess
I wanted to move the /home to be on the 16gb partition instead of the default which was on the 4gb with the installation.
 I copied/saved  /home to a temporary directory and then moved the contents of /home to the 16gb disk and mounted it on /home At this stage all seemed to be working correctly and applications worked as before. However when I rebooted it can not find my home directory, complains a lot, and if you bypass the messages ends up with a minimal GUI screen which does not respond to anything I tried. It seems that the 16gb disk is not being mounted.

How can I get into a terminal to allow me to reverse what I have done?

Phil

---

### Post by Dave_L on 2011-05-16
Have your tried booting into recovery mode, or booting from the Live CD?

---

### Post by newairly on 2011-05-16
I can not find how to start in recovery mode. Is it a key to hit during booting?

Phil

---

### Post by newairly on 2011-05-17
Managed to sort it out booting from the USB stick that I installed from.
Strangely though a few settings had been lost. Are they only saved on shutdown?

Phil

---

### Post by Dave_L on 2011-05-17
Booting into recovery mode is a selection in the grub menu.

By default, the grub menu only appears if you hold down the shift key (I think) during boot.

You can also force display of the grub menu by editing the file /etc/default/grub, commenting out a line:

```
#GRUB_HIDDEN_TIMEOUT=0
```

and then running update-grub to propagate the change to /boot/grub/grub.cfg:

```
sudo update-grub
```

-----

What settings did you lose?

---

