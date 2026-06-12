---
title: "Video driver problems"
date: 2009-09-26
forum: General Help
---

### Post by screaminfakah on 2009-09-26
Hello,
I screwed up X big time and have not been able to fix.  Heres what happened
I downloaded and manually installed the latest ATI driver for my laptop.  Everything worked great but then a month later I was fooling around with some stuff and accidentally enabled the ATI proprietary driver from System-Administration-Hardware Drivers.  It caused video problems so from the Recovery terminal I uninstalled the latest ATI drivers and was able to get to desktop.  Video was horribly slow and screwed up.
I read on another posting to uninstall all of the ATI drivers installed in Synaptic and reboot using the Fix X option to revert to the default driver.
Now I cannot get to the desktop no matter what I try.

Thanks,
Steve

---

### Post by Worp8d on 2009-09-26
Have you tried going into the GRUB boot menu, selecting recovery mode startup and then selecting the "try to fix graphics problems" (it's something like that) option?  I messed up my video settings and that fixed things up enough to get me back working with the system.

---

### Post by screaminfakah on 2009-09-26
Already tried that.

---

### Post by automaton26 on 2009-09-26
You say you originally did a manual install - have you tried doing the manual _un_install ?

For the latest Catalyst drivers, that means:

```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh

```

Once you're back to default drivers, do a manual install again.

---

### Post by screaminfakah on 2009-09-26
I already did the uninstall as you described. Then I was back at the desktop and video was slow.
That is when I uninstalled all of the ati programs in Synaptic.

---

### Post by cgroza on 2009-09-26
ahh..video problem are the most crapy

---

### Post by screaminfakah on 2009-09-27
Solved!

From the recovery Net root prompt I had to use this command

sudo apt-get install --reinstall xserver-xorg-core

Thank god for Google

---

