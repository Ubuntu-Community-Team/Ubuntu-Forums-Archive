---
title: "Installing Amazon's MP3 downloader"
date: 2012-07-20
forum: General Help
---

### Post by bkline on 2012-07-20
Amazon has installers for it's MP3 downloader on various Linux distros, including Ubuntu.  When I tried installing it on the current Ubuntu I got an error complaining about a missing package (libboost-filesystem).  So I installed the latest libboost-filesystem and tried again, but Amazon's package still wasn't happy: "Dependency is not satisfiable: libboost-filesystem1.34.1."  Anyone else wrestled with this?  Did you find a solution?

---

### Post by coffeecat on 2012-07-20
This thread is about getting the Amazon downloader to work in 10.04, but there are some comments about 12.04 towards the end of the thread:

[http://ubuntuforums.org/showthread.php?t=1478214](http://ubuntuforums.org/showthread.php?t=1478214)

My solution is to install Banshee with which you can browse the Amazon site, order using your Amazon account and it downloads your mp3's into your Music folder as soon as you have purchased.

---

### Post by bkline on 2012-07-20
> **coffeecat said:**
> This thread is about getting the Amazon downloader to work in 10.04, but there are some comments about 12.04 towards the end of the thread:

[http://ubuntuforums.org/showthread.php?t=1478214](http://ubuntuforums.org/showthread.php?t=1478214)

My solution is to install Banshee with which you can browse the Amazon site, order using your Amazon account and it downloads your mp3's into your Music folder as soon as you have purchased.

Thanks for the tips.  Didn't have luck with the 12.04 instructions, but your solution is working.  May also investigate pymazon, another package mentioned in the thread you pointed me to.

---

