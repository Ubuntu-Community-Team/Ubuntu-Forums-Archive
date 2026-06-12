---
title: "Synaptic Package Manager Problem"
date: 2010-03-23
forum: General Help
---

### Post by mskmeg on 2010-03-23
Hi everyone,

I am having some issues with the Synaptic Package Manager.  Every time I install a package, it shows the following error:

E: seamonkey-browser: subprocess installed post-installation script returned error exit status 2
E: seamonkey-mailnews: dependency problems - leaving unconfigured
E: seamonkey: dependency problems - leaving unconfigured
E: seamonkey-chatzilla: dependency problems - leaving unconfigured
E: seamonkey-gnome-support: dependency problems - leaving unconfigured

The packages seem to get installed properly though regardless of this error.

Does anyone have a solution to this issue?

---

### Post by dcstar on 2010-03-23
> **mskmeg said:**
> Hi everyone,

I am having some issues with the Synaptic Package Manager.  Every time I install a package, it shows the following error:

E: **seamonkey-browser: subprocess installed post-installation script returned error exit status 2**
E: seamonkey-mailnews: dependency problems - leaving unconfigured
E: seamonkey: dependency problems - leaving unconfigured
E: seamonkey-chatzilla: dependency problems - leaving unconfigured
E: seamonkey-gnome-support: dependency problems - leaving unconfigured

The packages seem to get installed properly though regardless of this error.

Does anyone have a solution to this issue?

Uninstall the packages that obviously did not install correctly.

---

### Post by mskmeg on 2010-03-24
Hi Dave,

I tried to install it using: sudo apt-get remove seamonkey-browser

This command gave me the following error:

dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing seamonkey-browser (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 seamonkey-browser
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Enigmapond on 2010-03-24
Have you checked in Synaptic to see if you can just remove the broken install? Custom tab and select broken on top...just a thought.

---

### Post by mskmeg on 2010-03-24
Thanks everyone for your help.  I found the solution to this issue at:

[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

After following the steps described on that site, I don't see any errors when upgrading or installing packages with Synaptic.

---

### Post by albasith786 on 2010-04-10
by using synaptic package manager, i installed gtalk. but the application is not shown in any main menu. how to use the package manager and the where the applications are actually installing

---

