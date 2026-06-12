---
title: "Unity not working."
date: 2011-05-29
forum: General Help
---

### Post by ryandushane on 2011-05-29
I just installed Ubuntu 11.04, and as soon as i reboot for the first time, it tells me that my hardware can not handle the Unity platform. I have an Asus UL30vt. It is new, and is a fast computer. It has switchable graphics, however i am not using my Nvidia card because i have tried the drivers for Ubuntu before, and they do not work. Anyways, i have tried the login screen settings and all that. I am clueless on how to fix this. :(

---

### Post by wildmanne39 on 2011-05-29
> **ryandushane said:**
> I just installed Ubuntu 11.04, and as soon as i reboot for the first time, it tells me that my hardware can not handle the Unity platform. I have an Asus UL30vt. It is new, and is a fast computer. It has switchable graphics, however i am not using my Nvidia card because i have tried the drivers for Ubuntu before, and they do not work. Anyways, i have tried the login screen settings and all that. I am clueless on how to fix this. :(Hi, if you system can run unity, you will need to install the nvidia driver from additional drivers because the nvidia is one of the most supported cards.Run this to check if your current video hardware/driver setup is able to run Unity, and what video driver is running:
```
/usr/lib/nux/unity_support_test -p
``` I know you will have to install the drivers before you check with this command, did it work when you tried the livecd? If so it is a matter of installing the drivers.

---

### Post by Ronalddig on 2011-05-29
Just run " Additional drivers " and download the nvidia driver. 
after reboot, you would be entered into Unity

---

### Post by ryandushane on 2011-05-29
It is a switchable graphics card.... I dont know if that has much to do with it. But i have tried installing the drivers on past Ubuntu versions, and it doesnt work. When i boot, it like opens Ubuntu in code. Its strange....... any ideas?

---

### Post by wildmanne39 on 2011-05-29
> **ryandushane said:**
> It is a switchable graphics card.... I dont know if that has much to do with it. But i have tried installing the drivers on past Ubuntu versions, and it doesnt work. When i boot, it like opens Ubuntu in code. Its strange....... any ideas?Hi,if you enabled your driver can you disable it?

---

### Post by ryandushane on 2011-05-29
Yes, but when i have it enabled, Ubuntu boots, into a code like environment. It does not boot into the regular OS. Its in a code like environment. It appears like the terminal does. Im clueless. It would be nice to use my graphics card on Ubuntu...... I love this OS.

---

### Post by linuxinstalledfromhdd on 2011-05-29
It looks like it should work ok with 10.10..  Natty is too new at this point to be sure. 

Here is a very handy writeup on 10.10 and your specific hardware:

[http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT](http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT)

Hopefully that helps. :)

---

