---
title: "The driver is activated but not currently in use"
date: 2011-04-22
forum: General Help
---

### Post by SuperUserDO on 2011-04-22
I can not get the Nvidia closed source driver to work..when i open the "Additional Drivers" it says that the driver is activated but not currently in use.
Another problem...I can not see my grub nor the Plymouth screen.please help
Thank You

---

### Post by grahammechanical on 2011-04-22
The drivers are working or you would not see any image on the monitor. The message means that you are not using the drivers for 3D or enhanced effects. I am using standard Ubuntu 10.10 and I get the message that the driver is activated and currently in use. I have enhanced visual effects activated in system>Preference>Appearance. In fact I am using the Compriz Config Settings Manager.

I am also testing 11.04 Beta and there I get the message "Driver activated but not currently in use." This is because I am using Unity2D. I am not using 3D or enhanced visual effects.

Regards.

P.S. Do you have more than one operating system installed. If not, then you will not see a Grub menu. Have you set the system for automatic log in? Then you will not see a log in screen.

---

### Post by tariban on 2011-04-29
I have the same problem. The drivers are not in use (I assume VESA is being used instead) and Plymouth is not showing the splash screen while Ubuntu boots up, however the login screen is showing up.

---

### Post by Mashepherd on 2011-04-29
I'm having the same issue, although i think i am using unity 3d because i have installed unity 2d and it doesnt seem to work as well as unity 3d

---

### Post by khughitt on 2011-04-29
Same thing here. Things seem to be working well enough though so I wonder if the driver is actually in use and it is just a bug?

---

### Post by lostnforest on 2011-04-29
Same here but I'm using Kubuntu instead.

---

### Post by spikoley on 2011-04-30
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207") on this issue.  Add your details to the bug report, so it will get fixed sooner.

It looks like this issue is caused by jockey (Additional Drivers).

---

