---
title: "Problem booting"
date: 2012-09-02
forum: General Help
---

### Post by Y u no boot on 2012-09-02
Hi I am trying to boot Ubuntu from a flash drive and got it to work on a different computer. It says 
[ 4.170204] [drm] nouveau 000:2:00.0: Parsing VBIOS init table 0 at offset 0x69B5

I have no clue what this means but it won't go past this.

---

### Post by pyro.xyz on 2012-09-02
Hello! Okay, I don't yet know enough to know what that error means, but I do know that generally (unless you have a really screwy computer) any bootable drive that you create should work on other computers. First off, what operating system are you using to create the bootable drive, and secondly, what operating system are you trying to boot Ubuntu on? Also, what types of computers are these? [Desktop/laptop with cd drive/netbook (laptop without cd drive)]

---

### Post by Y u no boot on 2012-09-03
> **pyro.xyz said:**
> Hello! Okay, I don't yet know enough to know what that error means, but I do know that generally (unless you have a really screwy computer) any bootable drive that you create should work on other computers. First off, what operating system are you using to create the bootable drive, and secondly, what operating system are you trying to boot Ubuntu on? Also, what types of computers are these? [Desktop/laptop with cd drive/netbook (laptop without cd drive)]

I'm using Windows 7 to create the bootable flash drive Trying to boot on Windows 7 but have only gotten it to work on a XP machine. I have yet to try it on another computer running Windows 7. I'm thinking that it should work on both, right? These are all Desktops by the way.

---

### Post by Y u no boot on 2012-09-03
I miss posted. This is Ubuntu not Lubuntu.

---

### Post by dragonfly41 on 2012-09-03
Try this .. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by nothingspecial on 2012-09-03
> **Y u no boot said:**
> I miss posted. This is Ubuntu not Lubuntu.

fixed :)

---

### Post by newb85 on 2012-09-03
Nouveau is the open-source nvidia driver.  It sounds like you did a persistent install on the USB and then installed the graphics drivers for one machine, which aren't working for your other machine.
Which of your machines have an Nvidia graphics card?

---

