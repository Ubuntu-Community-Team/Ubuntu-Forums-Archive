---
title: "Automatix - trashed GDM (or X)"
date: 2006-06-09
forum: General Help
---

### Post by fopetesl on 2006-06-09
I installed latest Automatix as per wiki instructions for Breezy.
Installed some codecs and Firefox 1.5.x

On reboot X failed to load with:
```
XIO: fatal IO error 104
```
so now I cannot log in at all.

Ran:```
apt-get -f install
```
and got a lot of 'cannot stat' messages many of which refer to  [http://theli.free.fr](http://theli.free.fr)

then```
apt-get update
``` comes up with similar 'cannot stat' messages.
Where to go?

---

### Post by an.echte.trilingue on 2006-06-09
That's why I don't like Automatix:  it does too much at once.  It's great if everything works, but if something buggers your system up it is really hard to know what did it and that makes it really hard to track the problem down.

_Warning: _ Only do this if nothing else works it might bugger your system.

What you can try is to out your installation CD in the drive, then ```
sudo cp /etc/apt/sources.
sudo vi /etc/apt/sources.list
```.  While that is open remove all the sources except for the CD.

Tip:  while in vi, press "i" to edit the text.  To save and leave, press ESC and then "wq" (then enter)

then, do this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```


Honestly, though, if you don't have too much invested in your current setup it might be easier to just reinstall, and next time install codecs by following [this page]("https://wiki.ubuntu.com/RestrictedFormats") and install firefox by following [this page]("https://wiki.ubuntu.com/FirefoxNewVersion?action=show&redirect=Firefox").  Just a thought.

---

### Post by fopetesl on 2006-06-09
Thanks, (interesting name), but somehow I fixed the problem.
I started in rescue mode and checked around the X logs without seeing anything helpful.
Typed [COLOR="Blue"]startx[/COLOR] and Bingo! Up comes GDM and into a (root) desktop.
Checked that Users were as I wanted, (no correction needed), and rebooted.
So far everything seems OK tho' where [COLOR="Blue"]wine[/COLOR] is....?

Thanks again, I'll bookmark this message for future investigation.:grin:

---

### Post by an.echte.trilingue on 2006-06-09
Thanks for the thanks!

---

### Post by stalefries on 2006-06-09
Did you have it install wine? Wine isn't a program that you run by itself, it's very much a kind of integration thing. If you want to run a windows program, either type "wine /path/to/your/windows/program.exe" or right-click it, select properties, open with, and add a new entry. Then for the new entry just type "wine". Then you can double-click any windows .exe file and run it!

---

### Post by sbassett on 2006-06-09
The best way to tell if wine is installed, is to run winecfg in a terminal (this should be your first bit of business anyway after installing it).

---

