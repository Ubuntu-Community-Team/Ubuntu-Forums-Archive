---
title: "I want the human theme back.."
date: 2010-04-30
forum: General Help
---

### Post by beefjerkymonster on 2010-04-30
Maybe only a handful of us liked it, but after using the old brown theme for a few years, I've becomed very accustomed to it. :(

How can I get it back?

---

### Post by IllegalCharacter on 2010-04-30
If you go to System->Preferences->Appearance it should be listed under the Theme tab.

---

### Post by wojox on 2010-04-30
No you have to open Synaptic and download it from the repo's. That's what I did. I like Human as well.

---

### Post by tmt345 on 2010-04-30
> **wojox said:**
> No you have to open Synaptic and download it from the repo's. That's what I did. I like Human as well.

I did that and it still doesn't look exactly the same, the the menubar is way too bright looking and the icons don't look the same.

---

### Post by beefjerkymonster on 2010-05-01
Well I installed the human theme from synaptic, and it looks great! The icons don't match however. Currently, the closest to the old icons is the "humanity" set (which is actually what the old set was, just an older version). This version of humanity has a bunch of purple mixed in, and doesn't really fit with my desktop. :/

How can I get that old version back? Where can I download the old humanity set from?

---

### Post by clhsharky on 2010-05-01
Easiest way, install U 9.10.

---

### Post by ubfu on 2010-05-01
dont just tell others , "install 9.10".Try to have some guide of having 9.10 theme back.Ubuntu is a way to config as you like.
I haven't install lucid yet but ai am sure there's a work around getting 9.10 theme back.
Actually , every new release of ubuntu should have an old them ready for those who dont want a major change of theme or any setting for beginner .

---

### Post by ubfu on 2010-05-01
[http://ubuntuforums.org/showthread.php?t=1421980](http://ubuntuforums.org/showthread.php?t=1421980)

---

### Post by beefjerkymonster on 2010-05-01
SUCESS! Everything looks 100% like 9.10 (besides login and shutdown).

The way I did it was install the human theme through synaptic. Then, to fix the icons, I found the icon set from 9.10 here: [http://packages.ubuntu.com/karmic/humanity-icon-theme]("http://packages.ubuntu.com/karmic/humanity-icon-theme")

I then extracted the "Humanity" and "Humanity-Dark" folders from it. Then I deleted the "Humanity" and "Humanity-Dark" folders in "/usr/share/icons/". Then I stuck the two folders that I extracted into "/usr/share/icons".

Yes, that was a bit of hack'n slash, but I wasn't sure how to install an older package and I didn't feel like learning how. :P

---

### Post by warjowuch on 2010-05-01
I guess you might take a look at gnome-look.org websites! BUt if you will find the exact ubuntu-the, I don't know. You might find a similar theme and tweak the colors

---

### Post by BlacqWolf on 2010-08-31
Open Terminal, and type

sudo apt-get install human-theme

---

### Post by Sciesch on 2010-09-16
I got a crazy idea (you need to use webspace for this)

1) Install  [Virtualbox]("http://wiki.ubuntuusers.de/VirtualBox/Installation")
2) Install gftp via Synaptic.
3) Download an 8.10 Intrepid Ibex Image and install it in Virtualbox. 
In Virtual Ubuntu: 
4) go to terminal and copy /usr/share/themes/Human to your Desktop
5) also copy /usr/share/icons/Human to your Desktop
6) zip the folders into one Archive
7) install gftp via Synaptic.
8) upload the Archive to some webspace
In Host Ubuntu:
9) Download the Archive :p

Now you got the original Human look at your hand, just extract and copy the folders to their respective locations. I recommend deleting whatever folders lurk around there under the names of Human. Have fun!

---

