---
title: "Compiz No Longer Runs"
date: 2010-07-05
forum: General Help
---

### Post by Precipitous on 2010-07-05
I have been running Lucid since it was in beta, and have never had any problems with Compiz. Now, all of a sudden it will not launch. If I try to run it from a terminal I get the following:
```
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```I am running an Intel 82915G/GV/910GL built in graphics controller, and when I run the compiz-check script everything checks out fine.

Does anyone have an idea as to where to go from here?

---

### Post by Precipitous on 2010-07-06
Is it possible that the video card has just been blacklisted? How does one find out?...

---

### Post by dabl on 2010-07-06
From Google:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442)

[http://ubuntuaddict.com/gnome-compiz-core-fatal-software-rendering-detected/](http://ubuntuaddict.com/gnome-compiz-core-fatal-software-rendering-detected/)

[http://ubuntuforums.org/archive/index.php/t-1018240.html](http://ubuntuforums.org/archive/index.php/t-1018240.html)

---

### Post by Precipitous on 2010-07-06
> **dabl said:**
> From Google:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442)

[http://ubuntuaddict.com/gnome-compiz-core-fatal-software-rendering-detected/](http://ubuntuaddict.com/gnome-compiz-core-fatal-software-rendering-detected/)

[http://ubuntuforums.org/archive/index.php/t-1018240.html](http://ubuntuforums.org/archive/index.php/t-1018240.html)

dabl - Thank you for you quick response. The first link seems the most relevant to my situation. I am at work right now, but will try the suggestions listed when I get home and will let you know the outcome...

---

### Post by Precipitous on 2010-07-07
> **dabl said:**
> From Google:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442)

[http://ubuntuaddict.com/gnome-compiz-core-fatal-software-rendering-detected/](http://ubuntuaddict.com/gnome-compiz-core-fatal-software-rendering-detected/)

[http://ubuntuforums.org/archive/index.php/t-1018240.html](http://ubuntuforums.org/archive/index.php/t-1018240.html)

I followed the advice in the first link and added the ppa for Intel Drivers, and installed all supplied updates...

I can now run Compiz, but am still unable to turn on any desktop effects. Anybody have any other ideas?

---

