---
title: "Weird Burning Flame on my  Desktop"
date: 2009-07-02
forum: General Help
---

### Post by glenn.w on 2009-07-02
Hi all,

This is probably an unusual question. A few weeks ago a strange burning flame appeared in the bottom right hand corner of my screen. I couldn't click on it or anything, it was just "burning" above my desktop switcher. The only way I could get rid of it was to reboot. It's back again today, now in the top right hand corner. 

See:

[http://yfrog.com/0wburningdesktop002p](http://yfrog.com/0wburningdesktop002p)
[http://yfrog.com/5wmoarflamep](http://yfrog.com/5wmoarflamep)

You obviously can't see it in a JPG, but the flames is animated (and freaking me out a bit).

Bit of extra info on what I'm running:
```
root@redtape:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy

root@redtape:~# uname -a
Linux redtape 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux
```


Any ideas?
Glenn

---

### Post by TeoBigusGeekus on 2009-07-02
Your pc is possessed!!!!:lolflag:
No, seriously, I think it's a compiz effect. Go to compiz settings and try to find it.

---

### Post by coffeecat on 2009-07-02
System > Preferences > Compiz Config Settings Manager. Under Effects, untick "Paint fire on screen".

What is odd is that to initiate the fire, you have to press shift + Windows key + left mouse button. Not a combination that's easy to do by accident. Is that what you did?

---

### Post by ju2wheels on 2009-07-02
Press SHIFT+WINDOWS KEY+C  to reset and clear it. Its a compiz effect as has already been stated.

---

### Post by glenn.w on 2009-07-02
Ahhhhh it was indeed a compiz flame, thanks so much guys, I was really worried I had some weird Linux malware taunting me. Doh! No idea how I managed to press ctrl + super + mouse1.

Flame successfully extinguised. Ta++

Glenn

---

