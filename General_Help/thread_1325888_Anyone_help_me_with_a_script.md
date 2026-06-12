---
title: "Anyone help me with a script?"
date: 2009-11-13
forum: General Help
---

### Post by sam_uk on 2009-11-13
OK these are the things I want to do. I am installing 50+ machines.

This will be my first script could anyone talk me through it?


#!
 
cd Desktop
 
wget [http://wirelessimage.pbworks.com/f/ubuntuguide.pdf](http://wirelessimage.pbworks.com/f/ubuntuguide.pdf)
 
cd /usr/share/backgrounds
 
rm warty-final-ubuntu.png
 
wget [http://wirelessimage.pbworks.com/f/warty-final-ubuntu.png](http://wirelessimage.pbworks.com/f/warty-final-ubuntu.png)
 
cd /etc/apt/

rm sources.list
 
wget [http://wirelessimage.pbworks.com/f/sources.list](http://wirelessimage.pbworks.com/f/sources.list)
 
wget -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
 
apt-get update
 
apt-get install sun-java6-jre sun-java6-plugin ubuntu-restricted-extras vlc wammu wine hfsplus hfsutils gnome-main-menu w32codecs adblock-plus ttf-mscorefonts-installer playonlinux ntfs-3g libdvdcss2 google-chrome-unstable lmms pidgin useragentswitcher skype gtkpod scribus-ng wormux


-----------------------

I am stuck on how to answer these questions using the script and make it non-interactive?

Example of a question that needs answering;
"After this operation, 250MB of additional disk space will be used.
Do you want to continue [Y/n]?"

How do I make it assume yes? 


--------------------------------------------------------

--------Open open-office--------

I don't know if it is possible to change this from the command line?
 
Go tools >options> general> load/save

Set to save as .doc .xls, and not warn when doing so.


Can anyone point me in the right direction?

---

### Post by wojox on 2009-11-13
#!/bin/bash

```
sudo apt-get install -y sun-java6-jre sun-java6-plugin ubuntu-restricted-extras vlc wammu wine hfsplus hfsutils gnome-main-menu w32codecs adblock-plus ttf-mscorefonts-installer playonlinux ntfs-3g libdvdcss2 google-chrome-unstable lmms pidgin useragentswitcher skype gtkpod scribus-ng wormux
```

---

