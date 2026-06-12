---
title: "Installing a 64-bit variant on a 32-bt Windows system using Wubi."
date: 2012-03-25
forum: General Help
---

### Post by Stormlord on 2012-03-25
Hi,

I am using a Windows XP Professional (32-bit) system and since that system is capable of running 64-bit OS's, I was wondering whether it would be ok to download a 64-bit Ubuntu variant and install it using Wubi.  Does Wubi come in 32-bit and 64-bit versions too?  Does the existing Windows OS have to be 64-bit too for a 64-bit variant to be able to get installed using Wubi?

Thank you!

:)

---

### Post by miasmablk on 2012-03-25
You can install a 64bit variant of Ubuntu using Wubi, I don't believe the windows OS's 32 bit architecture will have any bearing on your wubi install. although i would suggest downloading the 64 bit .iso and installing from a live cd instead.

 heres a link that can provide further info on 64bit installations using Wubi [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2012-03-25
Just to add to what miasmablk said... wubi.exe will default to the 64bit version of Ubuntu if your computer is 64bit (regardless of whether you're running 32bit windows).

You can also force a 32bit install by downloading the 32bit iso or by running wubi.exe with the *--32bit* option.

Wubi.exe (the installer) is 32bit, but the Ubuntu it installs can be either 32bit or 64bit as it boots independently (therefore not dependent on Windows, just the computer arch).

---

