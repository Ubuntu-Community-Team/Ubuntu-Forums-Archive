---
title: "Gnome or KDE applications on Xubuntu"
date: 2009-10-22
forum: General Help
---

### Post by UranUtan on 2009-10-22
Hi,

On a Pentium 3, 1 GHz, 768 MB RAM which runs Ubuntu 9.04 a little bit slow.
Next week, I would like to do a fresh install of Xubuntu 9.10 release. I have never used Xubuntu before and would like to know if Gnome's or KDE's application would run OK on Xfce.

In the case it is possible, would this install the Gnome environment and undo the purpose of having a light weight Xfce desktop environment?

And more generally, beside the Desktop environment, is there any application / OS feature from Ubuntu that Xubuntu cannot have? In other words, what would be the main inconveniences of running Xubuntu?

Thanks in advance for any help.

---

### Post by MelDJ on 2009-10-22
it will run but you will have to download and install kde/gnome libraries when installing

---

### Post by earthpigg on 2009-10-22
xfce is gtk, meaning GNOME and LXDE stuff will run without needing to install QT libraries.

when using QT stuff in gnome/lxde/xfce, the RAM overhead will be greater and they may or may not run slower. other than that, they will run fine.

[http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)
[http://en.wikipedia.org/wiki/Qt_%28toolkit%29](http://en.wikipedia.org/wiki/Qt_%28toolkit%29)

edit: also, having multiple desktop environments will not slow your computer down a bit as long as you have the hard drive space for it.

friendly reminder: linux filesystems only function properly if over 5% of space is free. this is the price we pay for never needing to defrag. run "df -Th" in a terminal from time to time and verify Use% remains under 95% for all filesystems.

---

### Post by UranUtan on 2009-10-22
Hi earthpigg,

Ws reading a few Xububtu vs Ubuntu comparison from various blogs & forum posts. It seems like Xubuntu is not that light. I will give it a try however just for the sake of seeing it myself.

Noticed Masonux in your sig and visited your site. Seems interesting, when will you have Masonux based on Ubuntu 9.10?

---

### Post by earthpigg on 2009-10-22
> **UranUtan said:**
> Hi earthpigg,

Ws reading a few Xububtu vs Ubuntu comparison from various blogs & forum posts. It seems like Xubuntu is not that light. I will give it a try however just for the sake of seeing it myself.

Noticed Masonux in your sig and visited your site. Seems interesting, when will you have Masonux based on Ubuntu 9.10?

xubuntu-desktop is not lighter than ubuntu-desktop or kubuntu-dsektop, but xfce4 *by itself* is.

for a bit more on the subject: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

the release of Masonux 9.10 will be a week or two behind the release of Ubuntu 9.10. 

if you are considering Masonux, please note that it does not include a lot of the ease of use packages that any of the *buntu-desktop metapackages do by default. you can certainly [add them]("http://sites.google.com/site/masonux/home/ease-of-use"), but for some that is to much.

---

