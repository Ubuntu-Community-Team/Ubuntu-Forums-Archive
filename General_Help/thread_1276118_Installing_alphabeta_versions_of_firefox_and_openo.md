---
title: "Installing alpha/beta versions of firefox and openoffice"
date: 2009-09-26
forum: General Help
---

### Post by spkays on 2009-09-26
I'm having issues installing openoffice 3.2 development version and the Firefox 3.6 version, code named Namoroka. Openoffice is a tar.gz file.I extract it and install it but it's missing the desktop integration folder. Anyone get around this?
I don't understand how to install Namoroka. It's a tar.bz2 file. I extract it and go to my terminal and try to change the directory to the firefox folder. It says it doesn't exist. I basically have no idea how to install something that's not an automatic install. I need to get past this dependency on auto installs. 
I like the idea of testing new products and being a more active part of the open source community. 
Any help would be greatly appreciated. 
I'm running the 64bit version of Ubuntu 9.04

---

### Post by Hagar Delest on 2009-09-28
There is no integration package in OOo development build because these versions are not stable enough for production. So to avoid the user using 'by default' such a version, the menus entries are not installed. You've to do it by yourself if you want but do it at your own risks.

---

### Post by MasterNetra on 2009-10-01
Try this: [http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html) follow the instructs and you can be using Firefox 3.6 or even 3.7 (if your so bold!)

As for Open office a tad bit of googling brought this up as well: [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

All via PPA. Firefox 3.6 (which is in beta) is named Namoroka and 3.7 is Minefield.

---

### Post by chucktryon on 2009-10-23
This is a bit of a cheat, but if you got to the directory, /usr/share/app-install/desktop, there are a bunch of "desktop" files there that you can copy to your Desktop directory to make shortcuts.  You still need to edit the properties to change "ooffice" to "/opt/ooo-dev3/program/soffice", but at least they give you the nice icons after you mark them as "trusted".

I'm guessing you could also copy them to the correct directory to get them to show up in the menus, but I haven't figured out yet where that is....

---

### Post by chucktryon on 2009-10-23
(Found it: Copy the openoffice-*.desktop files to the ~/.local/share/applications directory under your home folder.  You still need to use your favorite text editor to change the "ooffice" to the soffice path, but once you do this, they show up nicely in your Applications menu.  Remember that, if you do add official packages later, you will need to manually remove these files to avoid duplicate entries in your Applications menu.)

---

