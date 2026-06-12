---
title: "Custom Ubuntu Install"
date: 2011-04-21
forum: General Help
---

### Post by Jonny87 on 2011-04-21
I was thinking about creating a custom Ubuntu. Basically what I want to do I guess is use the Ubuntu OS as the base and add and remove packages so that I can do a normal install from a (edited) CD but the installation will be my own version of Ubuntu. Is this possible?

---

### Post by lmarmisa on 2011-04-21
You could use remastersys. This program is included in the Ubuntu repositories.

---

### Post by wojox on 2011-04-21
Download the mini.iso

It's the Ubuntu base. Then you can install X, a DE, WM.....

---

### Post by Jonny87 on 2011-04-22
> **lmarmisa said:**
> You could use remastersys. This program is included in the Ubuntu repositories.

I think I have tried the remastersys in the past but didn't seem to have much luck with it I guess unless someone has another idea I could try it again, I may have been missing something.

[QUOTE=wojox]Download the mini.iso

It's the Ubuntu base. Then you can install X, a DE, WM..... 	[/QUOTE]

Where can I get the mini.iso from? So it's just the base of the Ubuntu system isn't it? no gui or any other packages?

---

### Post by mastablasta on 2011-04-22
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
 
Minimal iso is indeed just the base. the installer is text based.
 
here is some guide on installing if you need it: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by K_45 on 2011-04-22
Consider the Debian net install CD, too.

---

### Post by LarsKongo on 2011-04-22
Install a command line (f4 on mini or alternate cd and select it from the menu.)
Before you install you should make a bash script that will install all the software you need. (That you can save on a USB, CD, partition.)

Here's a good base of useful software (That I think is useful.) No desktop environment though. ;)
```
#!/bin/bash
sudo apt-get update && sudo apt-get upgrade # Or dist-upgrade if you prefer that
sudo apt-get install build-essential xorg ttf-mscorefonts-installer python-software-properties # Python software properties are needed if you are going to add any PPA
```

If you then would like to add a DE like Gnome, KDE, XFCE, LXDE etc...

For example: A  minimal (but still quite useful) Gnome 2.32 setup in Maverick:
```
#!/bin/bash
# Installs a minimal Gnome 2.32 desktop with some useful software
sudo apt-get install gnome-core
sudo apt-get install gdm gdebi jockey-gtk file-roller unrar p7zip synaptic

# Installs software that can make the desktop to look a little prettier.
# You'll have to manually install any theme or desktop background you want though.
sudo apt-get install dmz-cursor-theme gtk2-engines gtk2-engines-pixbuf gtk2-engines-murrine
```
After that you can restart or start gdm. At boot up gnome-panel will complain about the fast user switch applet. Just remove it. You can install those things in Synaptic later if you like. Software like: *firefox, indicator-me, fast-user-switch-applet, light-themes (The default Ubuntu theme)* etc.

What browser you prefer may be individual. Personally I prefer Opera (which I don't belive is in the repositories atm) so I just wget it from their ftp. 
*wget [ftp://ftp.opera.com/pub/opera/linux/](ftp://ftp.opera.com/pub/opera/linux/) and then add version number + amd64 or i386 .deb file based on your install.*

Otherwise if you prfer to use the latest Firefox. :p
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get install firefox
```

If you are missing any software you can search for packages here:
[http://packages.ubuntu.com/maverick/](http://packages.ubuntu.com/maverick/)

---

### Post by lmarmisa on 2011-04-22
Try these two commands:

```

sudo remastersys clean
sudo remastersys dist

```

---

### Post by Jonny87 on 2011-04-22
Perhaps I should be slightly clearer, I not wanting install other packages during the install of the base system. I want to be able to modify the Ubuntu CD image so that the live cd is my own Ubuntu setup with its own package and will install as the custom set up. I don't completely rewrite the whole system, it will still be Ubuntu just a different range of apps that better suit me and other people I know.

---

