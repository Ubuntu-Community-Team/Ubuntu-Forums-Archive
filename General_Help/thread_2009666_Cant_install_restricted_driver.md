---
title: "Cant install restricted driver"
date: 2012-06-24
forum: General Help
---

### Post by searayman on 2012-06-24
Trying to install ATI/AMD proprietary FGLRX graphic drivers (post release update)

and It tells me to check out a log file. Here is what the log says:

[http://pastebin.com/RtLNZvXz](http://pastebin.com/RtLNZvXz)

---

### Post by searayman on 2012-06-24
bump, anyone? This is really frustrating. I can not use my second screen without the restricted drivers.

---

### Post by steeldriver on 2012-06-24
I never got the 'post-release' version to install on my 11.10 system - there are some suggestions for fixing the failed installation here:

[http://ubuntuforums.org/showthread.php?t=1966870&page=2](http://ubuntuforums.org/showthread.php?t=1966870&page=2)

Or you could try QIII's alternative instructions here:

[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

If neither of those work you may have more luck with the later drivers off the AMD/ATI website - people have reported problems building the local package for installation via dpkg/apt but the plain unmanaged install seems to work OK

---

### Post by nipunshakya on 2012-06-24
If there are two drivers listed, try to install the second one first (don't remember the name) and then try to install the post release.....

---

### Post by Mark Phelps on 2012-06-25
In general, installing the post-release drivers does not work.  Folks have better results installing the other drivers instead.

Also, I have an AMD video chipset and have no problem at all using dual monitors on the open-source Radeon drivers.

---

### Post by QIII on 2012-06-25
In pre-release testing, for as long as I have been doing it, the Radeon driver works flawlessly.

I'm currently using it on my Quantal test machine with dual monitors.

---

