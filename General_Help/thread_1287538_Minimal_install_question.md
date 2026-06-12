---
title: "Minimal install question"
date: 2009-10-10
forum: General Help
---

### Post by sigurnjak on 2009-10-10
Since i will be moving to a 9.10 Ubuntu i am planing to do a minimal install. However i have two questions .
1.  My wife likes showfoto and kolourpaint , both KDE apps . Is there a way to install them without pulling all  those dependencies .Something like this for Firefox works :
sudo apt-get --no-install-recommends install firefox-3.0

I do not have a test pc right now  so would this do :

sudo apt-get --no-install-recommends install showfoto

2. When next release comes out , is it possible to do a distro  upgrade with minimal install ?

---

### Post by scragar on 2009-10-10
Yes to both questions.

---

### Post by slakkie on 2009-10-10
> **sigurnjak said:**
> Since i will be moving to a 9.10 Ubuntu i am planing to do a minimal install. However i have two questions .
1.  My wife likes showfoto and kolourpaint , both KDE apps . Is there a way to install them without pulling all  those dependencies .Something like this for Firefox works :
sudo apt-get --no-install-recommends install firefox-3.0

I do not have a test pc right now  so would this do :

sudo apt-get --no-install-recommends install showfoto


Still available in karmic  (although for me it doesn't matter, since I run KDE so most of the recommends are probably installed).

> 
2. When next release comes out , is it possible to do a distro  upgrade with minimal install ?

Depends on what you mean.

If you mean, I did a minimal install and I want to do a network upgrade, yes that is possible. 

If you want to do a fresh install with the mini.iso on top of your current OS, yes, that would work.

If you mean, if I download the mini.iso, mount it and and want to perform an upgrade from that ISO, no that will not work, use the alternate CD instead.

---

### Post by sigurnjak on 2009-10-10
Wow guys ! That was fast ! Thank a lot .:)

---

