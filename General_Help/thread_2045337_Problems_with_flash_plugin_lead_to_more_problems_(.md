---
title: "Problems with flash plugin lead to more problems :("
date: 2012-08-21
forum: General Help
---

### Post by jake7 on 2012-08-21
I was having an issue with my flash player, so I tried to uninstall and reinstall it. I messed up somewhere along the way, now I cannot install or uninstall anything at all, manually or through the software center.

I try to hit the repair button when I'm given an error and this is what I get in response:


installArchives() failed: dpkg: dependency problems prevent configuration of nspluginwrapper:i386:
 ia32-libs (20090808ubuntu36) breaks nspluginwrapper (<< 1.4.4-0ubuntu2) and is installed.
  Version of nspluginwrapper:i386 to be configured is 0.9.91.5-2ubuntu2.
dpkg: error processing nspluginwrapper:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nspluginwrapper:i386
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of nspluginwrapper:i386:
 ia32-libs (20090808ubuntu36) breaks nspluginwrapper (<< 1.4.4-0ubuntu2) and is installed.
  Version of nspluginwrapper:i386 to be configured is 0.9.91.5-2ubuntu2.
dpkg: error processing nspluginwrapper:i386 (--configure):
 dependency problems - leaving unconfigured



I also searched and tried this in the terminal: sudo apt-get -f (or something similar I found in a different forum topic) in an attempt to fix the broken repositories. 

If it matters I'm running ubuntu 12.04 lts 64 bit version. I am new to linux in general so I'm sorry if this seems like a dumb question, but I did search for a couple of hours with no fix before I posted here.

---

### Post by TenPlus1 on 2012-08-21
It seems that you tried to install the 32-bit flash player and it has borked things due to the ia32-libs and nspluginwrapper conflicting with one another...

You could try and remove them both at the same time by doing:

sudo apt-get remove -purge nspluginwrapper ia32-libs

...and see if that helps, failing that I would recommend installing 32-bit Ubuntu for the sake of simplicity and that everything generally works...

---

