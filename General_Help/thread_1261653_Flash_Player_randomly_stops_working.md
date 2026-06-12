---
title: "Flash Player randomly stops working"
date: 2009-09-09
forum: General Help
---

### Post by Virtualboxbuntu on 2009-09-09
I am running Kubuntu Jaunty x86_64 with KDE 4.3, as is mentioned in my signature. 

I have Firefox, Konqueror, and Opera. Flash Player works on all of them. However, when I am using Flash Player to view something, it will stop working for no apparent reason. This can happen at any time while I am using Flash Player, and Flash Player no longer works in that particular browser until I close all instances of it. But it will still work in the other two browsers. This was also a problem for me in Gnome.

As much as I enjoy and prefer Linux, this greatly annoys me, and I must sometimes resort to my MacBook's Mac OS X to visit Flash sites without aggravation. Thank you for your time.

---

### Post by QIII on 2009-09-09
Can't remember if Kubuntu uses gnash or swfdec (I settled on Gnome several years ago...) but if it does, uninstall both.

They cause conflicts with Flash.

---

### Post by Mike_IronFist on 2009-09-09
> **Virtualboxbuntu said:**
> I am running Kubuntu Jaunty x86_64 with KDE 4.3, as is mentioned in my signature. 

I have Firefox, Konqueror, and Opera. Flash Player works on all of them. However, when I am using Flash Player to view something, it will stop working for no apparent reason. This can happen at any time while I am using Flash Player, and Flash Player no longer works in that particular browser until I close all instances of it. But it will still work in the other two browsers. This was also a problem for me in Gnome.

Thank you for your time.

Hi, can you give us a little bit of extra information?

-How did you install your flash player?

-What kind of graphics card do you have, and if it's NVIDIA or ATI, what driver do you have installed?

---

### Post by purry on 2009-09-09
For that you need to again download the flash player and re insall it make sure the above copy shoud be uninstall 1st for that you cab follow the link:.

[www.adobe.com/products/flashplayer/](www.adobe.com/products/flashplayer/) -

---

### Post by Virtualboxbuntu on 2009-09-09
It is Adobe Flash Player, I installed it by installing kubuntu-restricted-extras. I will try re-downloading, and as my signature says, it's a Nvidia card. 6150 LE to be precise.

EDIT: There seems to be a problem. The Adobe website has no 64 bit flash player for Linux. I am using Adobe Flash Player, and my system is 64 bit. How is it that it's installed already?

---

### Post by Vaphell on 2009-09-09
check about: plugins to see the version number
at adobe you can find 10.0.32.18

---

### Post by Virtualboxbuntu on 2009-09-09
about:plugins says that it is Shockwave 10.0 r32. The file names are different.

Firefox:        npwrapper.libflashplayer.so
Konqueror:  flashplugin-alternative.so
Opera:         /usr/lib/mozilla/plugins/flashplugin-alternative.so

---

### Post by QIII on 2009-09-09
The 64 bit version of Flash is an Alpha.

You can download and install from the tarball, if you are really in a hurry and want to deal with an Alpha.

The 32 bit version will work if you install from the repositories, which is how I suspect it was installed -- the flash plugin installer is installed.  10.0 r32 is release 32, which means you probably have the latest (10.0.32.18)

Again:  Check to see of gnash (I think that is Gnome, but I'm not sure) and swfdec are installed and uninstall them.

---

### Post by Virtualboxbuntu on 2009-09-09
> **QIII said:**
> The 32 bit version will work if you install from the repositories.
What is the name of the package?

---

### Post by QIII on 2009-09-09
flashplugin-installer.

---

### Post by Virtualboxbuntu on 2009-09-09
```
$ sudo aptitude purge flashplugin-installer

The following packages are BROKEN:
flashplugin-nonfree
```
Hmm, maybe that tells me something! In any case I purged then installed flashplugin installer, I will see how it works. But I have to go to work now, so I won't know for a while. Thanks for your help.

---

### Post by Virtualboxbuntu on 2009-09-10
My apologies for the slow reply. This does indeed seem to solve the problem, however I will test it further to ensure that. Thank you for your time.

---

