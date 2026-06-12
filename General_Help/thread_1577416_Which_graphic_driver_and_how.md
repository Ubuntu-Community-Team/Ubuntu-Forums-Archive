---
title: "Which graphic driver and how?"
date: 2010-09-18
forum: General Help
---

### Post by kjvee on 2010-09-18
Ok I reinstalled ubuntu and completely removed my windows partition :)

But I wanna know should I
1. Install proprietary driver from System > Administration > Hardware Drivers
2. or dl from nVidia website then install that.

and if #2, how do i install it?

---

### Post by formaldehyde_spoon on 2010-09-18
Just go #1. Less effort.

---

### Post by Such_is_life on 2010-09-19
Where do the options come from in System > Administration > Hardware. All I have is my Broadcom B43.  I need to install my NVIDIA driver, but I have tried for 2 solid days and have not been successful installing it or anything that works. What do I have to do to make it possible to install. (Geforce 6100).  Any help is appreciated.

---

### Post by sandyd on 2010-09-19
> **kjvee said:**
> Ok I reinstalled ubuntu and completely removed my windows partition :)

But I wanna know should I
1. Install proprietary driver from System > Administration > Hardware Drivers
2. or dl from nVidia website then install that.

and if #2, how do i install it?
you using 64 or 32 bit ubuntu.

---

### Post by Such_is_life on 2010-09-19
32 bit

---

### Post by sandyd on 2010-09-19
> **Such_is_life said:**
> 32 bit
```
[FONT=monospace]
[/FONT]sudo apt-get install envyng-core
envyng -t
```

---

### Post by Such_is_life on 2010-09-21
All in all it worked - thank you

---

### Post by Serpher on 2010-09-21
It is best to install the NVidea driver to get the most performance out of your card. If you go on their site you can easily find the driver you're looking for. When you have it (I'm assuming in your Downloads folder), press Ctrl + Alt + F1 and enter the following commands after logging in as root:

```
sudo /etc/init.d/gdm stop
ls Downloads
sudo sh Downoads/NVIDEA(etc etc etc)
sudo /etc/init.d/gdm start
```

---

