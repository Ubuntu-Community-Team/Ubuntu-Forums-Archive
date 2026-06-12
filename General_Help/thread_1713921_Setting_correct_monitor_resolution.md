---
title: "Setting correct monitor resolution"
date: 2011-03-24
forum: General Help
---

### Post by washable mist on 2011-03-24
I am currently using ubuntu on a desktop machine alongside a 19" monitor which is capable of outputting a resolution of 1280x1024 but the only resolution options in system > preferences > monitors are
1360x768
1024x768
800x600
To try and get ubuntu to run at a higher res i tried the guide here [http://ubuntuforums.org/showthread.php?t=284690](http://ubuntuforums.org/showthread.php?t=284690) which tells me to open up gedit and make some changes, my problem lies in xorg.conf which is empty.

i also tried the guide here [http://ubuntuforums.org/showthread.php?t=1112186](http://ubuntuforums.org/showthread.php?t=1112186) but could not get that to work bfor my resolution, can anyone help with this :-|

---

### Post by lithopsian on 2011-03-24
Before messing with xorg.conf, which has changed in recent versions of Ubuntu, read [this](https://wiki.ubuntu.com/X/Config/Resolution).  In particulat try the xrandr commands to set the resolution you want.  If you can make it work that way, it is possible to just include the xrandr command in your X startup and leave it at that.

---

