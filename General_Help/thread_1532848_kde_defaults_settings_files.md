---
title: "kde defaults settings files"
date: 2010-07-17
forum: General Help
---

### Post by jtGohan on 2010-07-17
Quick question on kde defaults

I'm trying to make a custom livecd for karmic with remastersys for a ready out of the box config and I cannot figure out how to set the following defaults:

windows decoration (kwin)
style
splash (ksplash)
login (kdm)
cursor (mouse theme)
wallpaper

The guides I searched for or only for kde3.5 I can't find any for kde4

Thanks

---

### Post by ankspo71 on 2010-07-17
Hi,
Much of your personal KDE4 configurations are stored in:
/home/<username>/.kde/share/config/

Most other kde related settings are stored in the parent folder:
/home/<username>/.kde/

You can copy any of these settings into the /etc/skel/ folder which will tell remastersys to use these settings as default for all future users of your remastered ISO. I think the directory structure needs remain intact too. Be sure you are not copying anything that you will consider private!
For example, make sure you don't put your kopete chat contacts in /etc/skel . Or passwords, bookmarks, network IDs, browser cache, etc.

For more information you can read this page:
_[http://remastersys.sourceforge.net/tips.html](http://remastersys.sourceforge.net/tips.html)_
Scroll down to read the sections:
"REMASTERSYS NOTES", 
"DISTRO PREP",
"COPY WORTHY CONFIG FOLDERS TO SYSTEM WIDE FOLDERS"

Hope that helps.

---

