---
title: "Wine problem"
date: 2011-08-31
forum: General Help
---

### Post by MareeSRB on 2011-08-31
Hello ubuntu forum

So far I have used Windows operating system, but when my graphics card burned, I have tried linux and works perfectly, not just the drivers for your graphics card instalirao.Medjutim when I want to install the Wine program, appears to me the following error (and you have a video below) :

The following packages have unmet dependencies:

wine1.3: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.0~ubuntu7 is to be installed
         Depends: libc6 (>= 2.11) but 2.13-0ubuntu13 is to be installed
         Depends: libgettextpo0 but it is a virtual package
         Depends: libglib2.0-0 (>= 2.16.0) but 2.28.6-0ubuntu1 is to be installed
         Depends: libgphoto2-2 (>= 2.4.10.1) but 2.4.10.1-2ubuntu5 is to be installed
         Depends: libgphoto2-port0 (>= 2.4.10.1) but 2.4.10.1-2ubuntu5 is to be installed
         Depends: libice6 (>= 1:1.0.0) but 2:1.0.7-1ubuntu1 is to be installed
         Depends: liblcms1 (>= 1.15-1) but 1.18.dfsg-1.2ubuntu1 is to be installed
         Depends: libldap-2.4-2 (>= 2.4.7) but 2.4.23-6ubuntu6 is to be installed
         Depends: libmpg123-0 (>= 1.6.2) but 1.12.1-3ubuntu1 is to be installed
         Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-2ubuntu0.1 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

Video:

[http://www.youtube.com/watch?v=bYzrQ9oxXj0](http://www.youtube.com/watch?v=bYzrQ9oxXj0)

Help plese ?

---

### Post by Enigmapond on 2011-08-31
Try running it from the terminal...it's so much easier...open terminal and do:

```
sudo apt-get install wine
```

I think you won't see these errors...

---

### Post by seawolf167 on 2011-08-31
As said above, see if the terminal command works for you

```
sudo apt-get update
sudo apt-get install wine
```

If that doesn't work, try

```
sudo apt-get install -f
```

then re-run the first commands

---

### Post by MareeSRB on 2011-08-31
I solved problem,but when i click on .exe file it just show on start bar Opening PhotoshopCS5.exe stands like that 10sec and then just closes..:(:(

---

### Post by Enigmapond on 2011-08-31
Well as far as I know, the only PS that works, and not well, in Ubuntu is CS3....but I may be wrong...have you tried GIMP? I use this professionally and it works great!

---

### Post by MareeSRB on 2011-08-31
Well i have some psd files that i need to open :( I watched this video and downloaded that version :

[http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

I will try GIMP and PS3 ;)

---

### Post by MareeSRB on 2011-08-31
sorry for double post but i installed Ubuntu on Serbian Cirlyic how can i return it to English USA.

---

### Post by Enigmapond on 2011-08-31
Yes you should have opened a new thread... Navigate to Administration/Language Support and change the top language to English...reboot.

---

### Post by MareeSRB on 2011-08-31
I am sorry :)

---

### Post by seawolf167 on 2011-08-31
> **MareeSRB said:**
> I solved problem,but when i click on .exe file it just show on start bar Opening PhotoshopCS5.exe stands like that 10sec and then just closes..:(:(

You'll want to take a look at [this link ]("http://wiki.winehq.org/AdobePhotoshop")for Adobe Photoshop in Wine, and [this link ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158")for CS5 specifically

---

