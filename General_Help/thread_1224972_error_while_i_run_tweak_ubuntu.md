---
title: "error while i run tweak ubuntu"
date: 2009-07-28
forum: General Help
---

### Post by venkatad on 2009-07-28
HI guys ....
THIS is my 1st post here. I really like Ubuntu esp jaunty with cool gnome-docky. I need u r help fixing this. When i try to install gnome global menu by using ubuntu tweak i get this error:
                                 

E: /var/cache/apt/archives/gnome-globalmenu-common_0.7.5-0ubuntu1~ppa1_all.deb: trying to overwrite `/usr/share/locale/zh_CN/LC_MESSAGES/gnome-globalmenu.mo', which is also in package gnome2-globalmenu-applet 
 E: /var/cache/apt/archives/gnome-globalmenu_0.7.5-0ubuntu1~ppa1_all.deb: trying to overwrite `/usr/share/doc/gnome-globalmenu/README', which is also in package gnome2-globalmenu-applet . i tried 2 days but couln't fix. i would appreciate if some one can help


thanx in adv

---

### Post by MelDJ on 2009-07-28
why not try going here? [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/) :popcorn:

---

### Post by venkatad on 2009-07-28
> **MelDJ said:**
> why not try going here? [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/) :popcorn: Tried did not work...

---

### Post by MelDJ on 2009-07-28
have you tried removing it? just uncheck it in ubuntutweak and just to be sure type 
sudo apt-get remove gnome2-globalmenu in terminal. Then try reinstalling it: sudo apt-get install gnome-globalmenu
or get the .deb package

---

### Post by venkatad on 2009-07-28
> **MelDJ said:**
> have you tried removing it? just uncheck it in ubuntutweak and just to be sure type 
sudo apt-get remove gnome2-globalmenu in terminal. Then try reinstalling it: sudo apt-get install gnome-globalmenu
or get the .deb package
Does not work when i try to remove gnome2-globalmenu thru terminal it says it has not been installed.

---

### Post by MelDJ on 2009-07-29
try installing an earlier version of it

---

