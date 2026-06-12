---
title: "Screen Resolution?"
date: 2009-11-20
forum: General Help
---

### Post by supernova42 on 2009-11-20
I am new to ubuntu and my screen resolution won't go above 800x600.  There are no drivers available in the Hardware Drivers. I have an integrated Nvidia Geforce 6150 LE.  Any thoughts?

---

### Post by HappyFeet on 2009-11-20
Try 
```
sudo apt-get install nvidia-glx-180
```

---

### Post by supernova42 on 2009-11-20
I got the response

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-180[/I]

any help?

---

### Post by mechro on 2009-11-20
In **System > Administration > Software Sources** have you got **Proprietary drivers for devices (restricted)** checked?

---

### Post by supernova42 on 2009-11-20
> **mechro said:**
> In **System > Administration > Software Sources** have you got **Proprietary drivers for devices (restricted)** checked?
It asks for my password but it says it is incorrect.

---

### Post by supernova42 on 2009-11-20
I got it to work but yes it is checked.

---

### Post by blegh on 2009-11-20
Look at this thread: [http://ubuntuforums.org/showthread.php?t=1313280&page=2](http://ubuntuforums.org/showthread.php?t=1313280&page=2)

Messing with xrandr fixed it for me.

---

### Post by supernova42 on 2009-11-20
That isn't fixing it for me but it did show me a lot of people have this problem. So if u know anyone who had this problem and fixed it please send theme here.  Also if it helps my monitor is an HP vs17e.

---

### Post by mechro on 2009-11-21
> **supernova42 said:**
> I got it to work but yes it is checked.

Then retry what HappyFeet said...

```
sudo apt-get install nvidia-glx-180
```

If that doesn't work try...

```
sudo apt-get install nvidia-glx-173
```

---

### Post by supernova42 on 2009-11-21
It worked but when I open up NVIDIA X server settings it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." so what should I do.

---

### Post by mechro on 2009-11-21
If you go to **System > Admin... > Hardware Drivers** does it give you the option to activate the driver? If it does then activate it. You may need to logout/login and/or reboot.

---

### Post by supernova42 on 2009-11-21
Congratulations Ubuntu God.  You solved it!!!

---

### Post by mechro on 2009-11-21
By the way, which one are you using - 180 or 173?

---

### Post by supernova42 on 2009-11-21
185.  Its the recommended one. (or so says ubuntu)

---

