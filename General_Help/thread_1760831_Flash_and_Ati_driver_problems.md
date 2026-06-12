---
title: "Flash and Ati driver problems"
date: 2011-05-17
forum: General Help
---

### Post by Naike on 2011-05-17
Hey.
What's the drawback of installing the ATI driver through the packet installer? Someone said that if I then update the kernel or something, the drivers are gone.

Also when I try to install Flash from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) using the Ubuntu 10.04+ option, and open it with AptUrl (apt:adobe-flashplugin?channel=$distro-partner) I get this error:
The channel 'natty-partner' is not known.

I guess that there is no natty flash plugin for firefox 4?
Anyway, it worked fine before I updated fierfox, now I don't have flash any more and I can't install it.

The second question regards the ATI drivers, how do I install the ATI driver package from ati.com on Kubuntu?
Their official PDF (nor the guide on ubuntu wiki) don't work, or well the commands they tell me to execute don't work.

---

### Post by charrah on 2011-05-31
Hi,

I couldn't comment on if the driver will survive a kernel update.

As for flash, you're probably better off installing it through the package manager. You said you're on KDE? Open up KPackageKit (in settings make sure you've checked off the boxes for universe, multiverse, and partner repositories). Then search for Flash and it should be the first one.

I used the guide here ```
http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually
``` though instead of creating and installing deb packages I just ran the installer manually because I couldn't get the packages working.

---

### Post by linuxinstalledfromhdd on 2011-06-01
You should give Flash Aid plugin a try:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

As for the driver try the wiki that someone else recommended.

> **Naike said:**
> Hey.
What's the drawback of installing the ATI driver through the packet installer? Someone said that if I then update the kernel or something, the drivers are gone.

Also when I try to install Flash from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) using the Ubuntu 10.04+ option, and open it with AptUrl (apt:adobe-flashplugin?channel=$distro-partner) I get this error:
The channel 'natty-partner' is not known.

I guess that there is no natty flash plugin for firefox 4?
Anyway, it worked fine before I updated fierfox, now I don't have flash any more and I can't install it.

The second question regards the ATI drivers, how do I install the ATI driver package from ati.com on Kubuntu?
Their official PDF (nor the guide on ubuntu wiki) don't work, or well the commands they tell me to execute don't work.

---

