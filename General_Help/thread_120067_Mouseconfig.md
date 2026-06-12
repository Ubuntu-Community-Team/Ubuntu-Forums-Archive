---
title: "Mouseconfig?"
date: 2006-01-20
forum: General Help
---

### Post by Freddy on 2006-01-20
Hi all.

I have tried several times to enable most of the buttons on my Logitech MX1000 mouse. I've used this HowTo for Gnome when making the the configurations that was needed to be done. [https://wiki.ubuntu.com/MX1000Mouse](https://wiki.ubuntu.com/MX1000Mouse)

I created a .xbindkeysrc which I put in my homedirectory but the only buttons that worked was my leftside buttons for back and fourth functions and with no sort of autostart. I need to type the command "xbindkeys &" in a Konsole for those buttons to work.

When doing a "sudo apt-get update" after that, something happens and this will be written out 
```
Bra http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Bra http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Ign http://wine.sourceforge.net binary/ Packages
Bra http://wine.sourceforge.net binary/ Packages
Fetched 7B in 1s (4B/s)
Reading packagelist... Finished
[1]+  Done                    xbindkeys
freddan@master:~$
```
and all of the buttons will work properly.

So my question is how I could make this work as it should from the boot of KDE, I have of course tried to put a symlink in "~/.kde/Autostart" to "/usr/bin/xbindkeys", it's not a permissionproblem cause I've tried to give myself full permissions to those files.

Plz, in dire need of help.   /// Freddan

---

### Post by mlomker on 2006-01-23
[QUOTE=Freddy]I have of course tried to put a symlink in "~/.kde/Autostart" to 
[/QUOTE]

Might I assume that the symlink was made executable?  It will ignore files that are not.

I wonder if KDE has to be running first?  You could try putting it at the end of /etc/init.d/bootmisc.sh

---

