---
title: "Minimal Ubuntu Set Up?"
date: 2009-10-05
forum: General Help
---

### Post by mckai on 2009-10-05
I'm still rather fresh when it comes to ubuntu. I'm interested in taking an old crashed dell inspiron 5150 and making it completely web-centric. I want to remove everything else that is not needed. 

I've already taken out games, but as I was deleting things... I realized I didn't know which was necessary for the computer to keep running smoothly!

Any suggestions would be wonderful =] I want it to surf the web and perhaps keep sound (so it can play pandora.com) and that's about it.

My question is: What can be removed?

Thank you very much in advance and have a great day!

---

### Post by tuxxy on 2009-10-05
I recommend you try Ubuntu Minimal ISO and you add only the packages you need rather than trying to remove them all.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by trstncmpbll on 2009-10-05
crunchbang lite if your ok with openbox, its completely stripped

---

### Post by c0mput3r_n3rD on 2009-10-05
> **tuxxy said:**
> I recommend you try Ubuntu Minimal ISO and you add only the packages you need rather than trying to remove them all.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


I agree, if you mess with certain applications with dependencies other applications have you can have a real head ache on your hand.  Ubuntu is only about 2.1Gb after install though any way.

---

### Post by earthpigg on 2009-10-05
> **trstncmpbll said:**
> crunchbang lite if your ok with openbox, its completely stripped

+1 for openbox for this task.

do a command line-only install, and install openbox and a couple other essentialls.

assuming you don't want wireless,

```
sudo apt-get install xorg gdm openbox firefox ubuntu-restricted-extras
```

i suppose that would do it.

when you reboot, you will get the normal ubuntu login screen that will take you to an openbox session.

the install above will probably use up about 800mb of hard drive space and well under 100mb of RAM at boot.

it also would not be hard to make it autostart firefox at login.

---

### Post by trstncmpbll on 2009-10-05
to slim down ubuntu you can also install rcconf and turn most things in the background off

---

### Post by tuxxy on 2009-10-05
> **trstncmpbll said:**
> to slim down ubuntu you can also install rcconf and turn most things in the background off

Well thats more aimed at services rather than packages and is really a front end for update-rc.d Many of these services could be disabled easily in startup applications.  Also disabling services wont necessarily remove much of the OS.  The Ubuntu Minimal should start off at around 20MB before you select and packages to install :D

---

### Post by trstncmpbll on 2009-10-05
look around google i came across a how-to article that told you every single thing on ubuntu that you can remove or disable safely. if you want a tiny os check out slitaz, its way better than tiny core linux, puppy linux, or dsl

---

### Post by trstncmpbll on 2009-10-05
i think this was it

[http://paulsdigitalworld.blogspot.com/2008/01/complete-ubuntu-speed-up-tweak-guide.html](http://paulsdigitalworld.blogspot.com/2008/01/complete-ubuntu-speed-up-tweak-guide.html)

---

### Post by JC Cheloven on 2009-10-05
> **trstncmpbll said:**
> look around google i came across a how-to article that told you every single thing on ubuntu that you can remove or disable safely. if you want a tiny os check out slitaz, its way better than tiny core linux, puppy linux, or dsl

SliTaz is really tiny, I loved it, but found it somewhat unstable. I'd go for puppy if a mini distro had to be the choice. Just my personal experiece, though.

Also I picked up this script: ```
#!/bin/bash
#######################################################################
# Ubuntu-Desktop-Minimal: Post-install script to install only the bare
#                         essentials of an Ubuntu Desktop.
#######################################################################
echo "[*] Installing Gnome Essentials"
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet \
human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork \
jockey-gtk gnome-screensaver gnome-utils
echo "[*] Installing Application Essentials"
sudo apt-get install -y gcalctool tsclient
```
It is intended to run it once the ubuntu minimal install cd has installed. You can then add epiphany (instead of firefox), vcl and vcl-plugin, and you'll get a system with the essentials (NM is there) but without any fat. 
I didn't try it yet myself, but I plan to. If you do (at your own responsibility, look first what it does), please tell us how it was.

---

### Post by Vock on 2009-11-21
I'm under the impression that the minimal cd mentioned here...


> **tuxxy said:**
> I recommend you try Ubuntu Minimal ISO and you add only the packages you need rather than trying to remove them all.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

will still install a lot of extra and unneccessary packages, the only difference between this and the normal installation disc is that using the minimal downloads all of the packages instead of getting them from the CD/USB key.

Is that true?

---

### Post by earthpigg on 2009-11-22
> **Vock said:**
> I'm under the impression that the minimal cd mentioned here...

will still install a lot of extra and unneccessary packages, the only difference between this and the normal installation disc is that using the minimal downloads all of the packages instead of getting them from the CD/USB key.

Is that true?

that is partially true. it will indeed download the packages at install time, but you can tell the mini.iso to do a command line only install, too.

it is more an outgrowth of the Ubuntu Alternate Installer CD than the standard Ubuntu Live CD.

---

### Post by animalprimate on 2009-11-22
-If your cpu can handle gnome and firefox, which is easy on the eyes.  My minimal web install is not unlike:

1. 
use alternate install disk and command line install option (configure /etc/network/interface if your eth0 doesn't connect)

2. 
sudo aptitude update; sudo aptitude safe-upgrade; sudo shutdown -r now

3. 
sudo aptitude install gnome-core gnome-system-tools gdm human-theme firefox-3.5

                    *note: this provides no fast-user-switch applet

-other things might want to install soon:

```

audacious           *listen to the music
vlc                 *watching movies duh!
brasero             *for if you got a cd burning drive
transmission        *to get torrents!
network manager     *you wanna do some network stuff?
gdebi               *you want gui for debi packages
file-roller         *you want gui for zips
gimp                *lets make pictures!
evince              *everyone reads pdf
jockey-gtk          *you want evil drivers!
gnome-screensaver   *who needs a screen saver?
gcalctool           *or use python to calculate

```
I hope that this is everything needed, I know it works.  I allways install this way.

---

