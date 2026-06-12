---
title: "Play on Linux constantly giving missing program message"
date: 2011-05-20
forum: General Help
---

### Post by samMD on 2011-05-20
Every time I start play on linux to use ms office this message keeps popping up before it. Is anything wrong or should be done ?

Thanks

---

### Post by samMD on 2011-05-21
bump

---

### Post by wildmanne39 on 2011-05-22
> **samMD said:**
> Every time I start play on linux to use ms office this message keeps popping up before it. Is anything wrong or should be done ?

Thanks

Hi,I have never heard of this program for running windows programs,as far as I know you have to use virtualbox or wine.I like virtualbox.

---

### Post by linuxinstalledfromhdd on 2011-05-22
sounds like a graphics issue. Maybe directX issue.  Try using winetricks.

sudo apt-get install winetricks

you will need to play around with the settings..  goodluck:D

---

### Post by samMD on 2011-05-30
sorry for the late response..graphics issues you say? 

so after installing winetricks is it a program  i can search for ?

---

### Post by linuxinstalledfromhdd on 2011-05-30
sudo apt-get install glxinfo

See if that fixes it?

---

### Post by ruffEdgz on 2011-05-30
> **linuxinstalledfromhdd said:**
> sudo apt-get install glxinfo

See if that fixes it?

I just installed this app yesterday, had the same error but needed to install the package 'mesa-utils':
```

aptitude install mesa-utils

or

apt-get install mesa-utils

```

---

### Post by linuxinstalledfromhdd on 2011-05-30
Same here.. I had to reinstall those as well. :)

---

### Post by samMD on 2011-05-30
thanks @ruffEdgz and everyone else those commands helped !

---

