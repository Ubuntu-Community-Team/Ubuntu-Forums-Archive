---
title: "Problem Installing playonlinux"
date: 2011-09-22
forum: General Help
---

### Post by dinkstopejaw on 2011-09-22
I'm trying to get playonlinux to work but it always fails on me.

It occurs when I type the command sudo apt-get install playonlinux, (This is after successfully running update commands for playonlinux etc.) or through simply trying to install through softwarecenter.

The error I get is:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine but it is not installable or
                        wine-stable but it is not installable or
                        wine-unstable but it is not installable
E: Broken packages

I've tried fixing these "broken packages" through synaptic, but there aren't any wine packages required to fix. 

I've spent hours trying to figure out the meaning of this message (wine-stable/wine-unstable aren't packages?) but I honestly don't know what I'm doing. Help would be really appreciated. 

I'm running 11.04 Natty Narwhal.

---

### Post by patryk77 on 2011-09-22
Sounds like you don't have updated caches, if it can't find wine. Is it a fresh install?

If so, try the following in the terminal:

apt-cache search wine
# Check if finds it
sudo apt-get update
apt-cache search wine
# Check again with new caches... If it's there now, perfect
sudo apt-get -f install
# If this installs it great, if it does nothing just install manually as it isn't broken
sudo apt-get install wine playonlinux

Hope that helps.

---

### Post by dinkstopejaw on 2011-09-23
I get this when I do the cache search, which seems to me wine caches are all up to date.

bonkersdolphin@bonkersdolphin:~$ apt-cache search wine
gnome-colors - set of GNOME icon themes
gnome-exe-thumbnailer - Wine .exe and other executable thumbnailer for Gnome
gnome-wine-icon-theme - red variation of the GNOME-Colors icon theme
q4wine - Qt4 GUI for wine (W.I.N.E)
pptview - view PowerPoint presentations
wine-gecko - Microsoft Windows Compatibility Layer (dummy package)
wine1.0 - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine1.0-dev - Microsoft Windows Compatibility Layer (Development files)
wine1.0-gecko - Microsoft Windows Compatibility Layer (Web Browser)
wine1.2-gecko - Microsoft Windows Compatibility Layer (Web Browser)
wine1.3-gecko - Microsoft Windows Compatibility Layer (Web Browser)
libkwineffects1a - library used by effects for the KDE window manager
playonlinux - This program is a front-end for wine.

However, after using the sudo apt-get install wine playonlinux command I get

bonkersdolphin@bonkersdolphin:~$ sudo apt-get install wine playonlinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

The same error comes up if I use sudo apt-get install playonlinux as before.
(I did run sudo apt-get update before all of this) Yes, this is a newly installed OS. 
Is it usually this much of a hassle to download playonlinux?

---

### Post by patryk77 on 2011-09-23
That is really weird.

I have a package called wine that installs (depends on) wine1.3 in Narwhal.

This might not work under Unity, the default interface, so log out, click your user name to log back in, when it asks for your password click Classic Mode to log into the GNOME interface, then go into System/Administration/Software Sources.

Enter your password if prompted, and check all the sources (main, universe, restricted, multiverse) if any are missing.

For me, "wine" is under Universe, so if that is not checked it would explain it.

Then click Close. If asked to reload, say yes (otherwise in terminal: sudo apt-get update)

Then try again:
sudo apt-cache search wine

You should hopefully have more packages listed, including the ones you are missing.

---

### Post by dinkstopejaw on 2011-09-23
Thanks patryk for all the help. I downloaded a wine repository and that seemed to fix the problem. (sudo add-apt-repository ppa:ubuntu-wine/ppa)

Afterwards, I had to do a clean reinstall anyways as I realized I did a bunch of other things wrong, and the second time through, playonlinux installed without any problems after simply running sudo apt-get update/upgrade.

---

