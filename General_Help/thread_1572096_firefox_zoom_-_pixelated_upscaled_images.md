---
title: "firefox zoom - pixelated upscaled images"
date: 2010-09-10
forum: General Help
---

### Post by nir8e on 2010-09-10
usually i use firefox with page zoom (125%)
after installing ubuntu 10.04 (firefox 3.6.8) i noticed a problem with the image quality
when the page is zoom.
after a quick search in google -> [_https://launchpad.net/~firefox-smooth-scaling/+archive/ppa_]("https://launchpad.net/%7Efirefox-smooth-scaling/+archive/ppa")
I ADD ppa:firefox-smooth-scaling/ppa to SOFTWARE SOURCES
and sudo apt-get install firefox.
the browser change his name from FIREFOX 3.6.8 to NAMOROKA 3.6.8
and the PIXELATED UPSCALED IMAGES WAS GOOD !!!
but the system updated firefox to 3.6.9
and now i have the same problem AGAIN ?
what to do ?

---

### Post by vek on 2010-09-16
I had the same problem, so I downgraded to the previous version.

For example, on the smooth scaling ppa, it says that the version there is called "3.6.9+build1+nobinonly-0ubuntu0.10.04.1+thjaeger1"

So after making sure I still had the PPA set up, I did this:
```
sudo apt-get install firefox=3.6.9+build1+nobinonly-0ubuntu0.10.04.1+thjaeger1
```

Note that installing a previous version of a package doesn't do it permanently - the next time Package Manager asks you whether you want to upgrade, it will offer the newer firefox, so make sure you uncheck it until they fix this.

---

