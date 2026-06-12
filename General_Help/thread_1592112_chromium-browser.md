---
title: "chromium-browser"
date: 2010-10-10
forum: General Help
---

### Post by bro on 2010-10-10
Since I upgrade to Maverick, Chromium-browser is no longer starting. It just says 'starting chromium...' for a while and then doesn't. I reinstalled to no avail. I get: 

```
$ chromium-browser
Attempting to load the system libmoon 
Segmentation fault
$ sudo apt-get install libmoon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmoon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by PaulW2U on 2010-10-10
I had the same problem with Chrome although I can't remember whether is was on my Lucid or Maverick installation. If you remove libmoon then Chrome/Chromium will probably start.

Do you _really_ need libmoon anyway? I know I don't.

---

### Post by petrasflorin on 2010-10-10
Have you tried sudo apt-get purge chromium-browser libmoon && sudo apt-get install chromium-browser libmoon ?

---

### Post by bro on 2010-10-10
A Thanks guys! I didn't even realize what libmoon was until I uninstalled it. No I don't need it, if I might need it is usually for something drm'nd that then still doesn't work. 

So I just ```
sudo apt-get purge libmoon
``` and that did it.

---

