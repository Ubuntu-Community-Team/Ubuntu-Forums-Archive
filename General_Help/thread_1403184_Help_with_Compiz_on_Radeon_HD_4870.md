---
title: "Help with Compiz on Radeon HD 4870"
date: 2010-02-09
forum: General Help
---

### Post by den160593 on 2010-02-09
I can't seem to get it to work. The default driver doesn't work. When I go to System > Administration > Hardware Drivers and install that driver my dual screens go very weird, with my right screen becoming default (instead of left) and my left screen having a vertical bar down half of it. I'm not sure why this is happening, maybe the xorg file? Or I dunno.

Could anyone help me get Compiz to work? Like the title says, I have a Radeon HD 4870 as my graphics card.

Thanks!!!

---

### Post by darolu on 2010-02-10
Try this program and let us know what it says:

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by den160593 on 2010-02-10
Hi,

Thanks for reply. This is the output:

>  Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4870]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


---

### Post by den160593 on 2010-02-12
Anybody at all able to help?

---

### Post by QIII on 2010-02-12
This is a suggestion, and a suggestion only.

A bit of background.  ATI used to be a horse's back side with regard to Linux support for their hardware.  So there was a day when open source drivers were the best bet.  It appears that you are using the "radeon" driver, which I believe is an open source driver.

When AMD bought ATI, they (being the little guy themselves) set about catching up in their support of Linux.  They didn't want to look at Nvidia's back side for the whole dog sled race.  They have come a long way, but still have a way to go.

They worked very hard to get a working driver into Karmic -- Catalyst 9.10.  I use it on my Karmic machine and it works flawlessly.  AMD/ATI is now in a mad scramble to do the same with Lucid because their current drivers do not work with the current X in Lucid.

Anyway.  To make a long story short...

You can try (but you are welcome to wait for the opinion of others) removing your current driver and installing Catalyst 9.10 from the Karmic repository.  It's there.  AMD/ATI made sure it was for the release of Karmic.

---

### Post by den160593 on 2010-02-12
Hey. Thanks heaps for reply!

I tried the ATI driver (via: System > Admin > Hardware Drivers) but that made my screens dodgy. So i tried installing a newer driver off the ATI website. But that was worse. So I uninstalled that. I tried to once again install the default included Proprietry driver via the Hardware drivers, but it's not there anymore (I want to run Compiz-check with that, maybe that might find the error. Or might be a xorg error, so someone might be able to help).

How can I reinstall that initial included driver? This is the error I get when booting with the System > Admin > Hardware Driver 's driver activated:

(EE) Missing PCS default file /etc/ati/amdpcsdb.default

I can still get in with low-graphics mode OR if I remove that driver (which I don't htink is there anymore) I can use it with default open source driver like i was before.

So how can I get that initial proprietry driver back? I have my install CD if needed.

Thanks!!!

---

### Post by QIII on 2010-02-12
Installing and uninstalling the fglrx driver can be problematic.  The URL below should help you get started.

Read it over before doing anything and ask questions.  Some one should be back by this thread before long.


[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by den160593 on 2010-02-12
I've done a clean reinstall cos I stuffed up trying to update my driver. This is the Compiz check now. How could I go about setting up Compiz. Thanks!

> denis-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4870]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use

---

