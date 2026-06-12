---
title: "Installed ubuntu, messed up screen"
date: 2011-08-13
forum: General Help
---

### Post by alcho+69 on 2011-08-13
I recently installed Ubuntu 11.04, I tried to boot it and it was like my windows screen before I restarted my computer however it was all jumbled and scattered everywhere, how can I fix this?

---

### Post by flipper T on 2011-08-13
so does the system just freeze with this jumbled screen displaying or does it go on to boot successfully ?

if unending freeze, i would try a reinstall, possibly using a different image of the distro

---

### Post by MG&amp;TL on 2011-08-13
Did you use wubi, or dual-boot (i.e. you burned a cd and changed BIOS)?

Just a quick reconnaisance question :D

---

### Post by alcho+69 on 2011-08-13
> **MG&TL said:**
> Did you use wubi, or dual-boot (i.e. you burned a cd and changed BIOS)?

Just a quick reconnaisance question :D

I used wubi


> **flipper T said:**
> so does the system just freeze with this jumbled screen displaying or does it go on to boot successfully ?

if unending freeze, i would try a reinstall, possibly using a different image of the distro

It goes into that screen right after its finished loading at the purple ubuntu screen

---

### Post by flipper T on 2011-08-13
as you are using wubi you can uninstall as you would any windows app.

i would try booting from a live cd to ensure that your hardware is compatible

---

### Post by bcbc on 2011-08-13
That sounds like a graphics card issue - what card do you have? Also what computer brand/model? 

You could try supplying 'nomodeset' as a boot option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by alcho+69 on 2011-08-14
> **bcbc said:**
> That sounds like a graphics card issue - what card do you have? Also what computer brand/model? 

You could try supplying 'nomodeset' as a boot option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I have an Nvidia Geforce GTS 360M 
It is an ASUS laptop but I am unsure of the model.

---

### Post by bcbc on 2011-08-14
Use nomodeset. Once booted check to see if there is a driver available for your card (press the windows key, enter Additional Drivers)

Refer to this bug report for more info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/657736](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/657736)

PS when you are installing with Wubi there are different instructions on how to supply nomodeset than when you are booting normally or with live CD. Wubi is described in post #8 and the others are in post #1 of this thread: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

