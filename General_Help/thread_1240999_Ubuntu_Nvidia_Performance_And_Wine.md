---
title: "Ubuntu Nvidia Performance And Wine"
date: 2009-08-15
forum: General Help
---

### Post by NightwishFan on 2009-08-15
I normally do not make generic threads like this, however I am sort of baffled at what I found out. I installed Battle For Middle Earth 2 in the latest Wine (1.1.27) on Ubuntu using the Nvidia 185 drivers. I found the performance to be pretty bad. I tried the same game on OpenSUSE. I am using the exact drivers from the installer and the same Wine version. Performance in OpenSUSE is noticeably better, even though it has an older kernel. I was running the game using a TWM minimal x window session on both platforms. AMD64 edition of both.

My specs:

AMD Athlon 2x Dual Core 3800+ 64-bit OS
890mb RAM
Nvidia 6150SE Nforce 430 (Integrated 128mb VRAM) Nvidia 185.35 driver.

Can anyone help me figure this out? Is Ubuntu modified in some odd way?

---

### Post by sdennie on 2009-08-15
From both distros, what is the output of:

```

uname -a
grep _HZ /boot/config-`uname -r`
grep EMPT /boot/config-`uname -r`

```

If it's a kernel difference, those commands will show the likely suspects.

---

### Post by NightwishFan on 2009-08-15
Thank you for the reply. I will likely have to get back to you on Monday (Easter time) for the results, as I am posting from a public place and not my home.

I believe that OpenSUSE uses more generic kernel settings and Ubuntu is geared to desktop use, but that should not cause this much performance impact.

OpenSUSE is about equal or greater to the performance of the game on Vista, and Ubuntu has trouble. Normally the opposite is true.

---

### Post by siegi on 2009-11-11
I have the same problem, i think. 
I had no problem playing gta san andreas on jaunty. (older nvidia driver)
But on karmic it's (not playable) slow.

Check this bug report.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/437526](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/437526)

---

### Post by NightwishFan on 2009-11-12
Karmic has seen improved performance for me actually. I can run the game on "Low" settings, which was actually unplayable in Vista.

---

### Post by GeoPirate on 2009-11-12
also are you using the beta or stable branch of wine? I've noticed improved performance and less crashes with the beta.  Also the nvidia version that ships with karmic is 185.18.36, so it might be differnt driver versions.

---

### Post by NightwishFan on 2009-11-12
In Jaunty I tried all the driver versions, including 180, 185, and 190beta. Performance was similar, I decided to stick with the stable 185. I used latest beta of Wine.

In Karmic, I am sticking to Wine 1.1.31 from the Ubuntu repositories. I will also use the Nvidia 185 driver from the repository. Performance in most games is adequate.

---

