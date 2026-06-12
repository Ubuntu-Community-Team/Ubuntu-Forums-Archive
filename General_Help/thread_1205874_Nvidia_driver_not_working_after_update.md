---
title: "Nvidia driver not working after update"
date: 2009-07-06
forum: General Help
---

### Post by dmiller40 on 2009-07-06
The biggest problem i have running ubuntu is my display driver. I have a Nvidia FX5200, now it's usually my fault when it stops working and it takes me hours to get it going again.

This time i was behind on my updates and installed like 75 of them, reboot and i'm in low graphics mode. There is nothing in my hardware drivers and nvidia-settings tell me to run nvidia-xconfig. It's like the driver disappeared or something.

I'm running Hardy Heron and was hoping someone could show me the easiest way to get this fixed. In the past i either accidentally figure it out or not sure which process actually fixes it.
thanks
dm

---

### Post by dmiller40 on 2009-07-06
So i reinstalled my nvidia driver (173.14.20) and i'm not in low graphics mode any more, which is good. But i can not change my resolution, it is set at 640x480. I see higher resolutions and i click and hit apply but it does not change.

In my nvidia settings 640 is the highest. xorg.conf says im using nvidia driver but boardname is vesa, not sure what that means. Also on the weird side i run XBMC and it starts and when in full screen mode is at 1024x720 resolution.

Any1 have an idea whats going on?
thanks
dm

---

### Post by dmiller40 on 2009-07-08
bump...

Still cant change resolution, using nvidia driver 172.14.20. Nothing showing up in hardware drivers.
Please help
dm

---

### Post by wojox on 2009-07-08
You're doing this through the nvidia x server settings?
System > Administration >

---

### Post by lukeiamyourfather on 2009-07-08
Are you using the binary drivers directly from nVidia? If you are, stop. Use the binary drivers in the repositories, enable them in the "Hardware Drivers" from the administration menu. Each time the kernel is updated it'll break the drivers directly from nVidia. The binary drivers directly from nVidia and the binary drivers in the repository are basically the same except for Ubuntu handles the kernel module for the graphics so it doesn't break after updates. Cheers!

---

### Post by dmiller40 on 2009-07-09
I was letting ubuntu handle the drivers and i needed to update the driver for some reason. Then updated ubuntu and it broke the driver. Now the driver does not show up in "hardware drivers" so i download from nvidia again.

I did get my resolution problem fixed, i just took an old xorg.conf and replaced my current one. But to keep this from happening i understand letting ubuntu handle the driver except it has disappeared from the hardware drivers window.

thanks
dm

---

