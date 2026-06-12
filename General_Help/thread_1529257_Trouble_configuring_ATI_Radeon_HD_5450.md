---
title: "Trouble configuring ATI Radeon HD 5450"
date: 2010-07-12
forum: General Help
---

### Post by mattgyver83 on 2010-07-12
Hoping there is someone out there who can help me with this.  Just purchased and installed an ATI Radeon HD 5450 graphics card and installed the proprietary drivers via System > Administration > Hardware Drivers.  After rebooting the machine X would not load so I restarted into recovery and removed my xorg.conf.  At this point I could restart normally and the machine would let me into X.

I went to System > Preferences > ATI Catalyst Control Center to try and configure the card and recieve the following message.

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI Driver is not functioning properly.
Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig.

So, i did just that, i restored my backup xorg.conf (configured for nvidia card) and executed 'sudo aticonfig --initial',  it made the proper changes and additions to the configuration file and this is what it looks like [[view xorg.conf]("http://pastebin.com/BUW4GQ8G")]

I then restarted the machine and X still refuses to begin [[view Xorg.0.log]("http://pastebin.com/qVzeC7sy")].  Again, I went in removed the xorg.conf file and the machine will load normally.  Does anyone have any idea how to fix this?  I tried running fglrxinfo to try and see if the card was properly installed and it just threw a segmentation fault.

Your help is greatly appreciated

---

### Post by youbantwo on 2010-08-12
thanks for posting this because I'm considering getting a 5450. Have you checked out this forum post? [http://ubuntuforums.org/showthread.php?t=1447659](http://ubuntuforums.org/showthread.php?t=1447659)

I thought this would have been fixed in the newer Ubuntu but I guess you still have to install the non synaptic package.

---

