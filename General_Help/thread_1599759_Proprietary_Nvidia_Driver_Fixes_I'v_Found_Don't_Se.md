---
title: "Proprietary Nvidia Driver Fixes I'v Found Don't Seem To Work"
date: 2010-10-18
forum: General Help
---

### Post by zenarcher on 2010-10-18
I've read most all the posts I can find on fixing the proprietary Nvidia driver issue with Kubuntu 10.10, but none seem to have worked for me, or I'm doing something wrong.

Here is what I have:
1) Fresh install of Kubuntu 10.10
2) Install latest Nvidia driver from "Additional Drivers"
3) Reboot system and following BIOS splash I get a blinking cursor for a few moments, then my monitor goes to sleep.  Nothing more.

Everything works fine with the crippled Nouveau driver until I install the proprietary Nvidia driver.  Most of the posts I've read say to go into GRUB at boot and edit, removing "quiet splash" and replace with "nomodeset."  I have done this, but still end up with the same situation above.

The only way I am able to get the system back up is to go into Recovery Mode at GRUB and delete /etc/X11/xorg.conf.  After doing so, the system will then boot up in low graphics, where I can remove the proprietary Nvidia driver through "Additional Drivers," reboot and everything is back to normal with the Nouveau driver again.

I have three systems, essentially the same with the same Nvidia cards and no matter what I do, I end up with the situation indicated above on all of them.  They all worked fine with Kubuntu 10.10 from Alpha 1 through RC, only getting this problem with the Final Release.

Perhaps I'm not doing something right, per the numerous posts I've read about this issue, or someone else has experienced this and has an answer which will resolve it.

Any assistance would really be appreciated, as the Nouveau driver is just not satisfactory for me.

Cheers,
zenarcher

---

### Post by NewDisciple on 2010-10-18
Here is the best way to install (at least for me) the latest driver. You may have to uninstall previous versions first. Then:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
Then:
```
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```
Then go to System > Administration > Hardware Drivers and make sure "Nvidia current" is activated.

---

### Post by zenarcher on 2010-10-18
> **NewDisciple said:**
> Here is the best way to install (at least for me) the latest driver. You may have to uninstall previous versions first. Then:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
Then:
```
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```
Then go to System > Administration > Hardware Drivers and make sure "Nvidia current" is activated.

Tried this and the latest Nvidia driver installed properly, but still have the same issue.  I can confirm, watching the hard drive activity light that the system appears to continue to run and load, even after the monitor goes to sleep.  Still doesn't seem to be a solution.

Thanks,
zenarcher

---

### Post by zenarcher on 2010-10-20
Well, it seems that the issue I have is with Nvidia GeForce 8xxx series video cards.  Installations work fine when done on a system with GeForce 6xxx series cards, but absolutely the same issue on three different systems using GeForce 8xxx series video cards.  Also, the install works fine with Intel video I have tried.  It seems to be specific to the one series of Nvidia video cards.

Cheers,
zenarcher

---

### Post by zenarcher on 2010-10-21
Apparently, between the Release Candidate and the Final Release, something was messed up regarding Nvidia GeForce 8xxx series graphics cards and the Nvidia proprietary drivers.  I'm not the only one with the issue and it seems to have something to do with the output not working with VGA but working with DVI output.  My KVM switches have VGA output only, so I can't switch to DVI, although I have DVI on my monitor and video cards.

[http://linuxtrends.com/an-ubuntu-10-10-upgrade-double-whammy/#comment-4550](http://linuxtrends.com/an-ubuntu-10-10-upgrade-double-whammy/#comment-4550)

Cheers,
zenarcher

---

### Post by efflandt on 2010-10-21
nvidia 256.53 drivers were used until initial RC, and sometime during RC that changed to 260.19.06, due to slow issues some people had (I think with GTX cards).  Do you maybe have an earlier CD (or iso) with the Ubuntu 256.53 driver package?

My GT 220 had no trouble with either version, but glxgears in 260.19.06 is 50% faster.

---

