---
title: "Can't install Xubuntu window manager"
date: 2006-04-05
forum: General Help
---

### Post by junglemike on 2006-04-05
Hi everyone. I've installed Ubuntu 5.04 cd with KDE.  For no doubt, it is beautiful window manager, kicks away any xp.
But my poor old laptop which is PII-300mhz/128mb ram, is really  slow. I would like to try XFCE window manager (which is Xubuntu, or isn't it ?) .
I follow these instruction of installing xubuntu here:
[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)
Everything was fine till the poing ```
sudo apt-get install xubuntu-desktop
```
Here's what i get: ```
 E: Couldn't find package xubuntu-desktop
```
By the way i am connected to internet via pcmcia wifi card. 
Is it looking the package on cd-rom disk?
If it is  - I'm in trouble, Cos I have only once pcmcia slot, and it is either internet, or cd-rom, but not both.
What should i do?

---

### Post by gingermark on 2006-04-05
I don't think the xubuntu-desktop metapackage existed in Hoary. Try 'sudo apt-get install xfce4' and see if that works.

If not, it'll be a repository issue. Type 'kdesu kate /etc/apt/sources.list', enter your password, and remove any '#'s at the beginning of lines. Save the file.

Then do sudo apt-get update and try again.

Hoary is a year old now - if it works for you then great, but you might want to consider upgrading to Breezy.

---

### Post by junglemike on 2006-04-05
Thank to you, I got it working.

---

