---
title: "help with 9.10"
date: 2010-07-22
forum: General Help
---

### Post by vikrantalmelkar on 2010-07-22
Hi There,

I have just upgraded from jaunty Jacklop to 9.10. there was no problem with the installation but now once it boots the mouse does not move. it is stuck at the center of the screen. i have tried using a usb mouse on my laptop but still no luck.

can someone please help with this situation.

all the help is really appriciated

---

### Post by vikas.sood on 2010-07-22
> **vikrantalmelkar said:**
> Hi There,

I have just upgraded from jaunty Jacklop to 9.10. there was no problem with the installation but now once it boots the mouse does not move. it is stuck at the center of the screen. i have tried using a usb mouse on my laptop but still no luck.

can someone please help with this situation.

all the help is really appriciated

I had this problem once with Intrepid. Mouse pointer used to freeze randomly.
You need to reload your mouse driver. Thats how i used to fix. You can try as well.

find out the kernel module for your mouse.
modprobe -l | grep mouse
sudo modprobe -r <kernel-module>
sudo modprobe <kernel-module>

be careful with modprobe -r :popcorn:

---

### Post by varunendra on 2010-07-23
Most probably it is a kernel related problem. Have you tried updating after installation? An updated kernel may have this bug fixed.

You can see your kernel version in System>Administration>System Monitor, or by following command:
```
uname -r
```

You should also mention your laptop's model no.

---

