---
title: "Performance issue."
date: 2011-12-30
forum: General Help
---

### Post by melrokz on 2011-12-30
Hi folks. I just installed Oneiric on my old PC and found it is slow. What is the best option to get a faster Oneiric?

My specs are:
Pentium 4
1GB RAM
40GB HDD
Intel 845 graphics

lshw output is attached below.

---

### Post by Paqman on 2011-12-30
Try switching to Unity-2D. Log out and click the little cog by your name on the login screen. If that doesn't help you might want to try switching from Gnome to a different desktop environment like XFCE or LXDE.

---

### Post by melrokz on 2011-12-30
What are the differences between LXDE and XFCE and which one will be easier to shift to? Will all GNOME apps work on these DE?

---

### Post by 3rdalbum on 2011-12-30
> **melrokz said:**
> What are the differences between LXDE and XFCE and which one will be easier to shift to? Will all GNOME apps work on these DE?

XFCE may be a little easier, but you can install both and switch between them to determine which one you prefer. Just switch between them at the login screen.

All Gnome apps work on all desktop environments, as do all KDE apps.

---

### Post by Paqman on 2011-12-30
> **melrokz said:**
> What are the differences between LXDE and XFCE and which one will be easier to shift to? Will all GNOME apps work on these DE?

LXDE is a bit lighter on resources than XFCE. I can't comment on which would be easier to shift to, as I haven't used LXDE for a couple of years and it's moved on a lot since then.

As for using Gnome apps on them, that would work fine. However, to run properly an app that's designed for Gnome would have to pull in a lot of Gnome dependencies to run. That means it could chew up quite a lot of RAM and be slow to launch (the same goes for using KDE apps on Gnome, and vice versa). Many apps aren't specific to one DE, but for ones that are it's best to not use them on a different DE if you're trying to keep performance sparky.

There are lightweight alternatives to all the regular Ubuntu desktop apps if this becomes a problem for you. Some of these will be the default apps included with Xubuntu or Lubuntu. For example, instead of using big fat Libre Office Writer you can instead use Abiword.

---

### Post by pip182 on 2012-01-02
I have tried the same combo recently. I believe this is an oneric hardware issue as the video system was extremely jerky even on moving the windows. 

Try the [X-Updates ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") and see if it fixes anything. 

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get upgrade 

But I dunno, try an older and lighter version like others have said. Maybe Mint 11 lxde. I tried it with cruchbang and it seemed to perform much better.

---

