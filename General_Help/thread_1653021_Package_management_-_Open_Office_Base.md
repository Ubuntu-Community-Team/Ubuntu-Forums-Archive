---
title: "Package management - Open Office Base"
date: 2010-12-26
forum: General Help
---

### Post by jburgess328 on 2010-12-26
Ok, I simply wanted to install open base on my ubuntu 10.04 installation but apparently its not that simple. I went to system>administration>update manager and it is telling me that it could not download all repository indexes, and that the method driver /usr/lib/apt/methods/httpe could not be found...

Things I have tried:

[LIST]
[*]Applications>Ubuntu Software Center, I tried to download it here but it did NOTHING
[*]System>Administration>Synaptic Package Manager, this fails to install it every time
[*][http://packages.ubuntu.com/](http://packages.ubuntu.com/), downloaded it from here and tried to install with GDebi Package Installer which also failed to work
[*]sudo apt-get remove openoffice*.*, followed by sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb, but this also gives me an error (and yes I did have the files extracted onto my desktop)
[/LIST]
So, could someone PLEASE instruct me on how to install open base on my system?!?!?

---

### Post by Hagar Delest on 2010-12-30
See here: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Note that you've to install the whole suite, not only Base. Most of the files are shared anyway, you won't spare any disk space.

---

