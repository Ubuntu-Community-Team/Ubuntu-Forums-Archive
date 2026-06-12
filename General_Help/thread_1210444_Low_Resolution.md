---
title: "Low Resolution"
date: 2009-07-11
forum: General Help
---

### Post by Lewis Smith on 2009-07-11
Hi,

I've just installed Ubuntu 9.04 on an external drive, and don't yet have internet acess from Ubuntu, I have to use Vista.

In 'Preferences > Display', I cannot set the resolution to anything higher than 800x600, although my screen is 1440x900. I think this may be due to a missing driver, but I don't know how to get it, and I would have to download it under Vista, reboot under Ubuntu, and then install it.

Has anyone else had a similar problem? If so, please tell me how to fix the problem/obtain the driver.

:confused:

Graphics Card: nVidia GeForce 6150 LE

---

### Post by fragos on 2009-07-11
System-> Administration-> Hardware Drivers and you will be offered one or more appropriate drivers from Nvidia. Rev 180 will work nicely. Now you will be able to select 1440x900 and get 3D acceleration as well.

---

### Post by Lewis Smith on 2009-07-13
There were no options in Hardware Drivers at the time, but thanks anyway.

I downloaded and installed the following:

dkms_2.0.21.1-0ubuntu3_all.deb

nvidia-173-kernel-source_173.14.16-0ubuntu1_i386.deb

nvidia-glx-173_173.14.16-0ubuntu1_i386.deb

and it appeared in Hardware Drivers. I pressed 'activate', and restarted, and the resolution was 1440x900, but as soon as I logged on, my screen said 'invalid input' or something along those lines, and I had to restart the PC manually, then select recovery mode and select the last option (fix graphics problems) it disabled the driver, and I am back to square one.

What should I do now?

---

### Post by fragos on 2009-07-13
I'm at a lose. 9.04 sensed my FX6200 and made the right drivers availble. The Hardware Drivers step is for drivers that aren't open source. Nvidia cards are well supported in Linux. Did you install from the Live CD or did you use the alternate install which gave perhaps to much control over what was installed? That might be your problem and your answer the Desktop Live CD.

---

