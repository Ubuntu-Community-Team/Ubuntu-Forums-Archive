---
title: "Gnome - KDE"
date: 2006-05-10
forum: General Help
---

### Post by JB_e on 2006-05-10
I am new to this and I was checking things out and after looking at both GNOME and KDE i like KDE better I am sorry if they question may have been asked before but I need help removing GNOME ubuntu and keep KDE Kubuntu. I have a fairly old computer and both environments are on it. How do I remove GNOME? 

Thanks..
~~>JB

---

### Post by dnm on 2006-05-10
Don't quote me on it, but I think:

sudo apt-get remove ubuntu-desktop

Will do what you want.

---

### Post by Sutekh on 2006-05-10
You should use this thread

[Ubuntu Forums - HOWTO Fully Uninstall the ubuntu-desktop meta-package](http://ubuntuforums.org/showthread.php?t=96046)

ubuntu-desktop is a meta-package that installs everything based on its large number of dependancies.  Removing ubuntu-desktop is not removing those packages.

---

### Post by jtibau on 2006-05-11
I think that unless you want disk space (everybody wants more disk space of course), it shouldn't make a difference (at least not much) to have both desktops installed, speed-wise I mean.
If you really want something faster for your old machine you should try another window manager. I've tried Xubuntu and found it to work much better on a 4 year old computer I still use for programming. It uses Xfce, instead of Gnome or KDE, which is tons lighter. I don't know how you can remove the ubuntu-desktop, I found about the meta-package thing while trying to do the same thing you are doing :) .
If you really want to get rid of ubuntu-desktop I think you should just backup all  your data and reinstall using a kubuntu cd.
If you really want a speed boost you should try Xubuntu though (there's a downloadable install cd also). It doesn't boast much eye candy but still looks neat and pretty user friendly. And since it is still ubuntu you can still have all your favorite software via apt-get

---

### Post by JB_e on 2006-05-14
I did it it was quite easy : [https://wiki.ubuntu.com/InstallingKDE](https://wiki.ubuntu.com/InstallingKDE)
just by using this website. It replaced everything Gnome. when I click on the KDE start button on the side it says Kubuntu 5.4. at start up no more Gnome environment.
         Another problem i have now is launching Akregator. after adding some new feeds last night i tried to launch it this morning several times but i never see it open at all. 
has this ever happen to anyone?
if so, how would i fix it?

---

