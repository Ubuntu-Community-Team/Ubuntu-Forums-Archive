---
title: "Installation of Radeon HD 4670 has failed"
date: 2010-07-07
forum: General Help
---

### Post by The Great Falcon on 2010-07-07
Hello

I tried this : [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to install my Radeon HD 4670's graphical drivers but it actually didn't work. I rebooted my computer and it says that the driver is not found and it makes the OS run on low graphics mode... I'm pretty new at Linux and running Ubuntu 10.04 Lucid Lynx...

I'd like to know either how I could make my thing use the default driver for my card (with which I was able to put the extra visual effects...) or how could I install the thing properly...

Thanks!

---

### Post by clhsharky on 2010-07-07
The Great Falcon

To get back to default OSS (Open Sourse Stack) driver,

```
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg
sudo restart gdm
```

Make sure "fglrx" is not listed in /etc/modules file.
Make sure no PPAs are enabled that is for video drivers.

Sharky

---

### Post by The Great Falcon on 2010-07-08
> **clhsharky said:**
> The Great Falcon

To get back to default OSS (Open Sourse Stack) driver,

```
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg
sudo restart gdm
```

Make sure "fglrx" is not listed in /etc/modules file.
Make sure no PPAs are enabled that is for video drivers.

Sharky

Hum... My terminal says that he cannot find the libgl1-mesa-glx package... Do I throw the whole thing by the window?

Thanks for help anyway \\:D/

---

### Post by The Great Falcon on 2010-07-08
Help?

---

### Post by The Great Falcon on 2010-07-10
110 views but no ones has an idea?

---

### Post by onecallednick on 2010-07-10
Which method did you actually use?  I have a Radeon HD 4200 (RV620) integrated into my mobo which i'm currently using.  I was able to install fglrx from the ubuntu repositories using the Hardware Drivers tool.  I messed it up somehow though by choosing to use unsupported updates.  Simplest way to try again IMO (and I'm also quite new) is to reinstall Ubuntu and try enabling the proprietary drivers again through the Hardware Drivers tool.  That's what I'm about to do, at least.  If there's a better way I'd like to hear about it too.

---

### Post by The Great Falcon on 2010-07-11
Hey! Thanks mate for talking about the Hardware Drivers tool. It made me look for it and I solved my problem! :) I clicked activate, it installed and rebooted to happily see the Catalyst Control Center in the System Menu :D 
Now I can enjoy those awesome effects :D 

For me, the problem is solved ^^

---

