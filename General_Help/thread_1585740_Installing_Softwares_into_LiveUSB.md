---
title: "Installing Softwares into LiveUSB"
date: 2010-09-30
forum: General Help
---

### Post by Youfan on 2010-09-30
Yesterday I created **Ubuntu 10.04 LiveUSB** using **Startup Disk Creator**. I've chosen *Stored in reserved extra space* so that every changes can be saved on the USB Flashdrive. And  it could run smoothly. But then when I wanted to install **Compiz Config  Setting Manager** using:

```
sudo apt-get install compiz config-settings-manager
```There's an error message saying that the server couldn't be found. I never change my **Software Source** configuration since it's a fresh-install, and the *Community-maintained Open Source software (universe)* on the **Software Source** is checked. Did  that mean that I couldn't install **Compiz Config Setting Manager** into my  bootable LiveUSB? And even more, did that mean I couldn't install any software into Ubuntu LiveUSB?

Is there any way I can install **Compiz Config Setting Manager** on my LiveUSB?

I'm thinking about installing my Ubuntu directly into my USB without using **Startup Disk Creator** (much like installing into Harddisk Drive), but I'm afraid my LiveUSB won't work on another (different) systems aside of mine.

Thank you very much for the reply.

---

### Post by andrewthomas on 2010-10-01
```
 
sudo apt-get update && sudo apt-get install compiz **compizconfig-settings-manager** compiz-fusion-plugins-extra

```
 
Try this and post the full output of any errors.

---

### Post by C.S.Cameron on 2010-10-01
My experience is that a full install will work on any machine as long as you don't install proprietary drivers, (ie Nvidia).

Compiz Settings Manager will work with a full install.

---

### Post by efflandt on 2010-10-01
If is said server could not be found it sounds like a network or DNS issue.  Does Firefox work fine web browsing?  If you need to use any proxy setting, you might want to crank that into System > Preferences > Network Proxy, so it would apply generally including retrieving packages.

---

