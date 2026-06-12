---
title: "Make USB bootable"
date: 2010-03-03
forum: General Help
---

### Post by Primefalcon on 2010-03-03
I've downloaded a livecd iso of fedora

rather than burning it to a cd I want to "burn" it to a usb drive and have the usb drive bootable....

how would I go about this...

I've tried extracting the files and copying them to the usb stick, and flagging the drive as bootable in gparted, but no go

---

### Post by chomps on 2010-03-03
The easiest way to do this is to use usb creator or even better UNetbootin.

You&#8217;ll first need to download the UNetbootin software and save it somewhere useful, since there&#8217;s no installation required, just double-click to run.

chose to use an already downloaded ISO image and then chose the flash drive, and click the OK button.

---

### Post by chomps on 2010-03-03
by the way you can get UNetbootin here:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by chomps on 2010-03-03
or just install it from synaptic package manager

---

### Post by wilee-nilee on 2010-03-03
If you want to install it with a persistent file, Fedora has a version of the Ubuntu USB creator.
[https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)

---

### Post by Primefalcon on 2010-03-03
I don't want to install it, just make a bootable usb instead of a cd...

unfortunately I've never had much luck with unetbootin and am looking at using the syslinux command atm

---

### Post by iponeverything on 2010-03-03
Try USB creator. 

It will make a bootable usb for you AND make so that you install from the usb if you wish. You seem to think it is one or the other.

---

### Post by Primefalcon on 2010-03-03
> **iponeverything said:**
> Try USB creator. 

It will make a bootable usb for you AND make so that you install from the usb if you wish. 
I did, it doesn't recognize the fedora 12 iso, with unetbootin it gets as far as trying to load the fedora image but then the screen goes weirdly fuzzy, weird thing is it works from a cd, same happened with openSuse

> **iponeverything said:**
> You seem to think it is one or the other.
I've been using Ubuntu for a 5 years, I think I know about installing from a LiveDisk.... So keep the snide thx

---

### Post by iponeverything on 2010-03-03
> **Primefalcon said:**
> I did, it doesn't recognize the fedora 12 iso, with unetbootin it gets as far as trying to load the fedora image but then the screen goes weirdly fuzzy, weird thing is it works from a cd, same happened with openSuse


When asking for help, don't you think that this would have been useful information?  

> 
I've been using Ubuntu for a 5 years, I think I know about installing from a LiveDisk.... So keep the snide thx

It would help others to help to help you, if you were clear.

---

### Post by wilee-nilee on 2010-03-03
All the usb loaders pretty much load the same thing. Unetbootin leaves no way of saving changes, usb creator does. They both, along with pendrive Linux just unpack the ISO so it can be booted and installed.

The only time it is a full install is if you from a live CD or thumb install the OS.

I used the Fedora loader just a couple of days ago on my MS set up, to load a thumb; worked fine.

I found the the Fedora 12 setup didn't let me set the resolution above 800x600 this not being auto-recognized for a better resolution, made it a deal breaker for me.

---

### Post by Primefalcon on 2010-03-15
I downloaded a pre-unetbootin configured OS, Android actually [http://code.google.com/p/live-android/](http://code.google.com/p/live-android/)

now this works perfectly in VirtualBox, but on a bare metal boot it gives the same weird graphical glitch on boot, must be a conflict or something with unetbootin and my specific machine...... which for reference is a dell e520 with an ATI 1300xt pro graphics card... weird

---

