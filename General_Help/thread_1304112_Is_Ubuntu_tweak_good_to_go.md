---
title: "Is Ubuntu tweak good to go?"
date: 2009-10-28
forum: General Help
---

### Post by arnab_das on 2009-10-28
Thats pretty much the question. have heard loads about ubuntu tweak and its abilities to install softwares not in the repos. has anyone used it? is it good/recommended?

---

### Post by fluffman86 on 2009-10-28
I've never had much luck with stuff like that.  If I need something, it's usually in the repositories, or else there's a PPA.  Worst case I just download a .deb file somwhere or have to compile from source, but that's VERY rare.

---

### Post by wilee-nilee on 2009-10-29
> **arnab_das said:**
> Thats pretty much the question. have heard loads about ubuntu tweak and its abilities to install softwares not in the repos. has anyone used it? is it good/recommended?

 Although karmic is set up to get the PPA's and the keys without the wget as per usual I think the tweak is a great tool if your lazy like me. It doesn't link you to every PPA but it has a few I like such as the Ubuntu Mozilla security team opera without a key gnome do, smplayer, chromium browser daily, the stable and unstable drivers PPA. The first thing I get after any install after opening all the backports etc is Ubuntu Tweak it has the medibuntu the restricted extras and many other regular down loads most people use, so with a few clicks my computer is up to date with the all that I want. Ubuntu Tweak has a stable and unstable PPA I always go for the unstable, it's Linux man I can always fix it or reinstall although I have never had a problem with the tweak.

---

### Post by scouser73 on 2009-10-29
> **arnab_das said:**
> Thats pretty much the question. have heard loads about ubuntu tweak and its abilities to install softwares not in the repos. has anyone used it? is it good/recommended?

Yes, I have used Ubuntu Tweak since Hardy Heron was released and it's always been an invaluable application to have. You can download Ubuntu Tweak from GetDeb - [[COLOR="Red"]**GetDeb: Ubuntu Tweak**[/COLOR]]("http://www.getdeb.net/search.php?keywords=ubuntu+tweak")

---

### Post by Uncle Spellbinder on 2009-10-29
or you can add the Ubuntu Tweak 0.5.0 PPA to you sources.lest...

```
##Ubuntu Tweak 0.5.0
deb http://ppa.launchpad.net/tualatrix/ubuntu-tweak/ubuntu karmic main 
#sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0624A220
```

---

### Post by konqueror7 on 2009-10-29
i recommend ubuntu tweak for those who are starting and some those (as said above) lazy:D... its a great tool, for getting all done after a install...:D

---

### Post by Oldbones on 2009-10-29
> **Uncle Spellbinder said:**
> or you can add the Ubuntu Tweak 0.5.0 PPA to you sources.lest...

```
##Ubuntu Tweak 0.5.0
deb http://ppa.launchpad.net/tualatrix/ubuntu-tweak/ubuntu karmic main 
#sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0624A220
```

the, "sudo apt-key adv...", command timed out several times before it finally worked. FYI

---

### Post by fragos on 2009-10-30
I highly recommend Ubuntu Tweak and have used across a number of releases. I particularly like the way it offers 3rd party repositories and sets them up for use. It has other configuration capabilities as well that aren't that easy set without Ubuntu Tweak.

---

