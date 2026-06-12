---
title: "TTY1 - 6 freezes system"
date: 2010-04-30
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2010-04-30
I usually log in to a tty as soon as I login to gnome so if I do have to go to it the music doesn't stop and what not but any time I press ctrl+alt+F1 - 6 the system freezes and I have to REISUB... I didn't notice it happening before these last set of updates but not sure if I ever used a tty at all since moving to Lucid. Side note... the reason I found this is because nvidia stopped working since as well.

---

### Post by Sin@Sin-Sacrifice on 2010-04-30
bump

---

### Post by spoon_ on 2010-04-30
Hey I had the same problem. Maybe this sequence of events will help someone debug it:

- I install lucid, and try to install official nvidia drivers. So I press CTRL+ALT+F1 -- switching to tty1 works fine so far.
- Nvidia driver fails to install.
- Going back to tty7, I read up about why it failed to install... turns out I have to blacklist nouveau and get rid of some nvidia packages. So I do this.
- I try to install nvidia driver again by pressing CTRL+ALT+F1, but at this point it fails like you mentioned and I have to reset my system.
- When it reboots, CTRL+ALT+F1 is still not working so I can't install the nvidia driver.
- I reboot to recovery mode, install the nvidia driver from there (it installs successfully), and now CTRL+ALT+F1 works fine again.

---

### Post by Sin@Sin-Sacrifice on 2010-04-30
apt-get install nvidia-current or the one from nvidia.com?

---

### Post by spoon_ on 2010-04-30
> **Sin@Sin-Sacrifice said:**
> apt-get install nvidia-current or the one from nvidia.com?

The one from nvidia.com

---

