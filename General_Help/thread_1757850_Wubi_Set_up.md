---
title: "Wubi Set up"
date: 2011-05-13
forum: General Help
---

### Post by anthonywastrinh on 2011-05-13
Hello,
When I was installing wubi (Ubuntu 10.04) on my windows 7, it started to download a amd 64 iso instead of an intel.  my computer is an intel.  at the end of setup it say cannot recieve files, check (a txt document in yr temp folder).  what should I do??

---

### Post by bcbc on 2011-05-13
amd64 just means 64bit - it's not well named. Wubi will choose 64bit if you computer is 64bit (you could still be running 32bit windows).
You can force it to install 32bit ubuntu if you want. See the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#Can I force Wubi to download and install a 32 bit version of Ubuntu?") for more info.

If you want to see why the last install failed, open windows explorer and enter %temp% in the address bar. Then look for the file wubi-xx.xx-rnnn.log (for 11.04 it's wubi-11.04-rev211.log). Post it here (press # above to post it between [CODE]tags ) if you need help

---

