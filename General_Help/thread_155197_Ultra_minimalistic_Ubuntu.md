---
title: "Ultra minimalistic Ubuntu"
date: 2006-04-04
forum: General Help
---

### Post by Muffe on 2006-04-04
I have an old laptop (PII 266 MHz, 96 MB RAM, 2 GB HDD) that I want to run linux on. I have fallen in love with Ubuntu, but I'm not sure if that's the right choice for that PC.

Is it possibe to make an ultra-minimalistic Ubuntu install? I will use the PC for only one purpose; surfing the internet. So what I basically need is X and a browser. Nothing more. And I have to keep the memory usage low, very low. I have used linux on daily basis the last three years, and I don't need graphical configuration tools and things like that.

Is this possible to do with ubuntu?

---

### Post by John.Michael.Kane on 2006-04-04
[http://www.watsky.net/](http://www.watsky.net/)   <----BeatrIX Linux
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)  <---DSL
[http://featherlinux.berlios.de/](http://featherlinux.berlios.de/) <----FeatherLinux
[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu) <--Lite Version.

---

### Post by bionnaki on 2006-04-04
do a server install
& then install fluxbox

---

### Post by NeghVar on 2006-04-04
BeatrIX is a great distro but since the founder is 'missing' it has become dead, although they do have a follow up progect. I would suggest either XUbuntu or DSL, Bea is fine for just surfing but it is outdated and caters very much to the new user that has never used Linux before.

---

### Post by ivan.virtuale on 2006-04-05
Use Xubuntu or server install with some other desktop environment.

---

### Post by Ubuntuud on 2006-04-07
I wouldn't install a heavy desktop like XFCE, fluxbox looks like a better idea

---

### Post by aysiu on 2006-04-07
[QUOTE=Ubuntuud]I wouldn't install a heavy desktop like XFCE, fluxbox looks like a better idea[/QUOTE] XFCE isn't a heavy desktop, but you're right--Fluxbox is much lighter than even XFCE.

---

### Post by djlosch on 2006-04-07
i did a server install, updated my repository, then got the .9 breezy fluxbox .deb thats floatin around the forums.  i apt-get installed xdm and xserver-xorg-core.

then i do a startfluxbox and i get an:
Error: Couldn't connect to XServer

where to from here?

---

### Post by draenor on 2006-04-19
You need to start X window system before running fluxbox. 
Type sudo startx and then there should be some terminal (if you installed one I guess) and from there you can run startfluxbox.

---

### Post by NetMatrix on 2006-04-19
When you do a server install X is not installed by default.  You have to install it first:

```
sudo apt-get install xserver-xorg
sudo apt-get install x-window-system-core
```

You may have to run through a couple of configs (I don't remember) and then you can :

```
startx
```

NOTE:  You can install gdm or kdm if you want a GUI log-in.  Also I would recommend installing the kubuntu-desktop package, as you can use some of the apps in fluxbox.  

```
sudo apt-get install kubuntu-desktop
```

What you want to do, I have done and am typing on that very system right now!!!

---

### Post by ivanhelguera on 2006-04-20
If you happened to be intersted in something that is not Ubuntu, I strongly recommend Puppy Linux. VERY impressive distro, boots live from CD, can be HD-installed. And a fast one.
In my opinion it's better for standard use then, say, DSL. But them again, DSL  is Debian-based, which is an advantage.

> Also I would recommend installing the kubuntu-desktop package, as you can use some of the apps in fluxbox. 

Is this a good idea? I've heard K-apps are hard on dependencies and K loads a lot of services. I would be interested in opinions,

---

### Post by NetMatrix on 2006-04-20
You could install ubuntu-desktop if you're worried about kde apps being to resource intensive.

---

