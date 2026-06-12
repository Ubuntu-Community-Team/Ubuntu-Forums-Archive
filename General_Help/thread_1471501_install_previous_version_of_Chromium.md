---
title: "install previous version of Chromium?"
date: 2010-05-03
forum: General Help
---

### Post by holadebob on 2010-05-03
My latest update (this am) included a chromium update. Chromium now will not do much, gets hung up on most searches, can't access gmail and a few other misc strange things so I thought I would try to go back a version, since it is in .archives. I deleted the current version 5.0.393, and trying installing the older version, and it said it wouldn't cause a newer update is available.

I tried reinstalling the newer version again, with no luck. 

Anyone tell me how to install a previous version?

Thank you.

---

### Post by wojox on 2010-05-03
Have you downloaded the one from the repo's?

```
sudo apt-get install chromium-browser
```

---

### Post by holadebob on 2010-05-03
This is the response from sudo get-install chromium-browser

Reading package lists... Done
Building dependency tree       
Reading state information... Done
chromium-browser is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev fakeroot x11proto-xext-dev libatk1.0-dev debhelper
  intltool-debian x11proto-kb-dev libglib2.0-dev x11proto-xinerama-dev
  libpango1.0-dev g++-4.4 x11proto-render-dev libxi-dev libxrender-dev
  po-debconf libstdc++6-4.4-dev libcairo2-dev libxdmcp-dev libsysfs-dev
  libdirectfb-extra libpng12-dev libfontconfig1-dev libmail-sendmail-perl
  libdirectfb-dev x11proto-composite-dev xtrans-dev x11proto-core-dev gettext
  libxcursor-dev cvs x11proto-randr-dev x11proto-damage-dev
  libxcb-render-util0-dev libxext-dev libjpeg62-dev libxdamage-dev
  x11proto-input-dev libfreetype6-dev x11proto-fixes-dev libpthread-stubs0-dev
  libxau-dev dpkg-dev libpthread-stubs0 libxcomposite-dev libxrandr-dev
  libexpat1-dev html2text libpixman-1-dev libxft-dev libx11-dev patch
  libxcb-render0-dev libxfixes-dev libxcb1-dev libxinerama-dev
  libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by wojox on 2010-05-03
Did you already install from the repo's or from a ppa?

If it's a ppa uninstall it and install the one in the repo's.

---

### Post by holadebob on 2010-05-03
This version of chromium came via the normal ubuntu update through the update manager that I do about everyday. I'm a newbie, so I don't know which of those, ppa or repo was used. My software sources for chromium show it is a ppa, so I guess that was what ubuntu used to get the update. How do I get it from repo?

---

### Post by PC_load_letter on 2010-05-03
> **holadebob said:**
> My latest update (this am) included a chromium update. Chromium now will not do much, gets hung up on most searches, can't access gmail and a few other misc strange things so I thought I would try to go back a version, since it is in .archives. I deleted the current version 5.0.393, and trying installing the older version, and it said it wouldn't cause a newer update is available.

I tried reinstalling the newer version again, with no luck. 

Anyone tell me how to install a previous version?

Thank you.

+1. 

I'm running 9.10 (Karmic) 64 bit here, and the latest PPA daily build (installed last Sat. night 5/1) had many severe problems, couldn't load my gmail page, and in some cases, starting Chromium caused my session to suddenly terminate and took me straight to the login screen.

To the other post, maybe it's me, but I don't see chromium-browser anywhere in the Karmic repos, am I missing something here?

---

### Post by wojox on 2010-05-03
Yeah nevermind. I thought you were using Lucid 10.04. Sorry ](*,)

---

### Post by holadebob on 2010-05-03
PC_load_letter. Whew, thank you for responding, I thought I was fighting a virus or something weird going on here, cause I looked around and didn't see any Chromium problems on the boards.

Well, I'll just use Firefox until Chromium folks get their act together. It would be nice to be able to delete the present installation of a program and go back to the previous version, since the program still exists in .archives. 

Bob

---

### Post by mc4man on 2010-05-03
> since the program still exists in .archives. 

Not sure what archives you're referring to 

Anyway you may be able to go back thru synaptic, search chromium browser
 
Try highlighting it -> package -> force version
You'd also need to do for chromium-browser-inspector and chromium-codecs-ffmpeg
If you can then after setting all 3 click 'apply'

After it's done close synaptic - when closing synaptic will ask if you wish to exit with changes still marked - choose yes
(otherwise synaptic will update you back to latest

Otherwise - if you can gather the 3 older packages - 
put them in a folder (creating an empty folder on your desktop will suffice) - cd to the folder in a terminal and run

```
sudo dpkg -i *.deb
```

---

### Post by holadebob on 2010-05-03
Thanks, Mc4man, I was referring to /var/cache/apt/archives/
I will try your method in a couple of minutes - I'll let you know

---

### Post by holadebob on 2010-05-03
Hey, I'm back with chromium version 5.0.391 and it works like it should - nice and smooth, good fix. thanks for teaching me that process with Synaptic, Mc4man, good job.
Bob

---

### Post by PC_load_letter on 2010-05-03
Unfortunately I'm not as lucky, the "Force Version" option is greyed out and I can't click it. Any ideas why this is the case?

---

### Post by PC_load_letter on 2010-05-03
I found the previous version in /var/cache/apt/archives and installed it w/ dpkg.
By the way, there are far more people experiencing all sorts of problems w/ Chromium even w/ Lucid, check here:
[http://ubuntuforums.org/showthread.php?p=9227965](http://ubuntuforums.org/showthread.php?p=9227965)

---

### Post by tg3793 on 2012-09-13
> **mc4man said:**
> Not sure what archives you're referring to 

Anyway you may be able to go back thru synaptic, search chromium browser
 
Try highlighting it -> package -> force version
You'd also need to do for chromium-browser-inspector and chromium-codecs-ffmpeg
If you can then after setting all 3 click 'apply'

After it's done close synaptic - when closing synaptic will ask if you wish to exit with changes still marked - choose yes
(otherwise synaptic will update you back to latest




Your solution is over two years old and still worked like a charm. Thanks Mc4man





.

---

