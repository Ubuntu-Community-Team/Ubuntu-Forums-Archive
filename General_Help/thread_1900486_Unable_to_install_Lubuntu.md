---
title: "Unable to install Lubuntu"
date: 2011-12-26
forum: General Help
---

### Post by rng on 2011-12-26
I tried to install Lubuntu on a pc where earlier ubuntu 9.04 and 10.10 were running properly (512 mb ram; reasonably fast processor, I think dual-core). The installation process started well, asked all options, but after some 'copying files..' it got stuck with screen showing blue wallpaper shades and a mouse cursor (movable) in form of a watch. I had to switch off the computer. On switching on, the hard disk partition had all folders (I do not know about the files but at least grub folder did not have required files) and basically Lubuntu did not install properly. I want a stable distro and I think I will continue with Ubuntu.

---

### Post by Rubi1200 on 2011-12-26
What make/model computer do you have and, other than RAM, what graphics card is installed?

---

### Post by rng on 2011-12-26
It has usual graphics card- not nvidia.

---

### Post by rng on 2011-12-27
Guess what! I tried again today and it installed very well. I am now writing from Lubuntu. It seems more responsive than ubuntu. The only difference in installation today was that instead of choosing install from boot menu, I started Lubuntu and started install application from desktop.

---

### Post by Rubi1200 on 2011-12-28
Glad you got things sorted out.

Enjoy :)

---

### Post by TroN-0074 on 2011-12-28
instead of re install the distro you could just type in therminal
```
$sudo apt-get install lubuntu-desktop
``` That would install Lxde and you could just switch on your GDM session selector
Same if you want KDE just type ```
$sudo apt-get install kubuntu-desktop
```
and if you want Xfce just do ```
$sudo apt-get install xubuntu-desktop
```
alternatively you can fire up your Synaptic Package Manager and do a search and get the desktop manager of your choice from there.
You should also look for vary windows managers that look very slick aswell and are very light weight.
Keep in mind each desktop manager comes with some embedded applications that you might no want in your system.
Enjoy LXDE and Have fun. 
Good luck to you!

---

### Post by rng on 2011-12-28
I see in the lubuntu login options kde also, but it does not run on choosing it. I guess I need to install kubuntu-desktop as mentioned above.

Also can I install kde-trinity or kde3.5 desktop? Is it supported here?

---

### Post by TroN-0074 on 2011-12-28
> **rng said:**
> 
Also can I install kde-trinity or kde3.5 desktop? Is it supported here?

It will install KDE 4.x.x I dont know what is the latest version. You can look in Synaptic. Do a seach for kubuntu-desktop. It will give you a brief description.

Keep in mind that if you install KDE it will put lot more app in your system. KDE comes with all the QT libraries needed for Amarok, Okular, kwallet, Konqueror and a bunch of other things.

Good luck to you.

---

### Post by amjjawad on 2011-12-29
> **TroN-0074 said:**
> instead of re install the distro you could just type in therminal
```
$sudo apt-get install lubuntu-desktop
``` That would install Lxde and you could just switch on your GDM session selector

Installing lubuntu-desktop is NOT like installing Lubuntu normally :)
Writing this from tons of tests and personal experience. Some other members of my team (Lubuntu) also share the same opinion with me.

---

### Post by amjjawad on 2011-12-29
> **rng said:**
> It has usual graphics card- not nvidia.

```
sudo lshw -C display
```

will tell you which Graphic Card you have :)

---

### Post by rng on 2011-12-29
@amjjawad: Thanks for the tip.  Please help me on my other thread also (I am not able to use HP laserjet 1020 printer on Lubuntu): [B][http://ubuntuforums.org/showthread.php?t=1901626](http://ubuntuforums.org/showthread.php?t=1901626)

[/B]Otherwise, Lubuntu rocks.

---

