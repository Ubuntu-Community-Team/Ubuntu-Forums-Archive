---
title: "Selecting Shutdown, logs out but doesn't shutdown the computer"
date: 2012-03-05
forum: General Help
---

### Post by ghetto2ivy on 2012-03-05
As above. My wife's HP G7-1150 works great except when she chooses shut down, it logs out instead. Even when there are no programs running, she still has to hold down the power button to get the laptop to turn off.

Any thoughts?

---

### Post by Neill_R on 2012-03-05
I had    the same problem with an HP n5271 laptop  here is what I did to solve my problem


this is for GRUB2 the latest version of GRUB
#
# to ensure power off on shut down
#
# gksu gedit /etc/default/grub
#
# make GRUB_CMDLINE_LINUX_DEFAULT="acpi=force lapic quiet splash"
# then run 
# # sudo update-grub --output=/boot/grub/grub.cfg
#

---

### Post by ghetto2ivy on 2012-03-11
Thanks. Tried adding "acpi=force lapic" and no improvement so far. 

Shutdown leads right to the login screen, and never past it.

---

### Post by synaptix on 2012-03-11
Have you tried shutdown via terminal and see if it produces the same result?

```
sudo shutdown -h now
```

---

### Post by ghetto2ivy on 2012-03-18
I did try from the terminal and the same result would happen. 

I ended up downloading the beta of Precise and foudn that the issue was gone in Precise Pangolin.

I installed the beta, and the issue is gone. Now everything works fine. Whatever it was 12.04 Beta 1 has fixed it.

---

