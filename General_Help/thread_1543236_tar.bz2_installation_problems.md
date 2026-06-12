---
title: "tar.bz2 installation problems"
date: 2010-07-31
forum: General Help
---

### Post by SchizmWolf on 2010-07-31
Hey folks. I noticed that I'm consistently having the same problem whenever I try to manually install a tar.bz2 file (for example, Vuze install package.) It works fine for the first bit with "tar -xvfj filename.tar.bz2," but when I cd to the file and try ./configure, make, or make install, it returns that there is "no such file or directory" even if there is a makefile.  Any ideas???

---

### Post by lovinglinux on 2010-07-31
Not all tar.bz2 files need to be compiled. I don't know about Vuze, but for instance Firefox distributes ready-to-run binaries as tar.bz2, which should only be extracted.

You should get the installation instructions from the web site where you obtained that file. Additionally, unless you have a good reason to download software from web sites, you should use only the repositories, for safety reasons.

To install Vuze with the command below:

```
sudo apt-get install vuze
```

---

### Post by SchizmWolf on 2010-07-31
Thanks for the info. I'll need to do a little poking around to make sure I get this installed right. I tried the repos first like you suggested, but the version it installed was out of date and wouldn't work (Vuze in my repos is at v.2.0.8 when the current version is 4.4) Thank you for the help though, and hopefully I can get more ejumacated on this kinda stuff :)

---

### Post by lovinglinux on 2010-07-31
> **SchizmWolf said:**
> Thanks for the info. I'll need to do a little poking around to make sure I get this installed right. I tried the repos first like you suggested, but the version it installed was out of date and wouldn't work (Vuze in my repos is at v.2.0.8 when the current version is 4.4) Thank you for the help though, and hopefully I can get more ejumacated on this kinda stuff :)

All you need to do is extract the vuze tar.bz2 file and click the vuze file (without extension) inside the extracted folder. I just tested it here and it works.

Nevertheless, I would recommend other BiTorrent clients, like Deluge, KTorrent and qBitTorrent. I'm currently using the last one and is the fastest client I ever used.

---

