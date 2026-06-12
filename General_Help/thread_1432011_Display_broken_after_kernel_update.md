---
title: "Display broken after kernel update"
date: 2010-03-17
forum: General Help
---

### Post by Nevon on 2010-03-17
After updating to version 2.6.31-20-generic, my desktop computer with an ATi HD4850 graphics card, using the fglrx driver, now won't boot to X. It goes through the boot process and displays the splash screen, but after that there is nothing on the screen. Choosing an older kernel version from GRUB doesn't make a difference. 

So... How do I solve this? I don't even know how to diagnose the problem properly. I can boot into recovery mode and get to the command line, however, starting x from there only leaves me with a blank screen.

EDIT: Ok, so the source of the problem is that I had installed the catalyst driver from amd.com, which needs to be reinstalled with every kernel update. I didn't know this in advance, so now I'd like a way to revert back to fglrx from the repos. Sadly, the community docs only seem to cover the graphical way of doing this, which is kind of useless to me at the moment.

EDIT2: The ATi driver docs gave me a way to uninstall the catalyst driver using only the command line. So now I've booted back into Ubuntu and selected to install the fglrx driver from System &#8594; Hardware Drivers. However, now when I boot up, I get the message: "(EE) Unable to initialize PCS database
(EE)  Missing PCS defaults file /etc/ati/amdpcsdb.default
(EE) No devices detected."

---

### Post by coffeecat on 2010-03-17
If you delete or rename (better, in case you want to refer to it later) your /etc/X11/xorg.conf file from a root console in recovery mode and then reboot, the xserver will default back to the open source ATI driver. No 3D or gee-whiz effects, but it'll give you a GUI to work from.

Good news for the future. I gave up on fglrx with my HD4200 graphics in Karmic - complete disaster - and relied on the open source driver. I'm testing Lucid on the same machine and compiz works out of the box with the open source driver. You probably don't get enough acceleration for gaming but it's plenty good enough for all the effects in compiz. Nice to see transparency again. You may have the same luck with your ATI card. There's only 10 days or so over a month before Lucid goes final. Worth testing.

---

### Post by Nevon on 2010-03-17
> **coffeecat said:**
> If you delete or rename (better, in case you want to refer to it later) your /etc/X11/xorg.conf file from a root console in recovery mode and then reboot, the xserver will default back to the open source ATI driver. No 3D or gee-whiz effects, but it'll give you a GUI to work from.

Good news for the future. I gave up on fglrx with my HD4200 graphics in Karmic - complete disaster - and relied on the open source driver. I'm testing Lucid on the same machine and compiz works out of the box with the open source driver. You probably don't get enough acceleration for gaming but it's plenty good enough for all the effects in compiz. Nice to see transparency again. You may have the same luck with your ATI card. There's only 10 days or so over a month before Lucid goes final. Worth testing.

I'm already in a graphical environment now. I just had to uninstall the catalyst driver. I guess what I'm using right now is the open driver, as I have basic system functionality. I don't really care about compiz, but I would at least like to be able to watch high res movies - which I ironically enough can do on my shitty laptop with an integrated intel chip, but not on my desktop with an HD4850 card.

Currently I'm reinstalling the catalyst drivers, as the proprietary one from the repos doesn't seem to work anymore. If it means I have to reinstall it with every damn kernel update, I guess that's what I'll have to do.

EDIT: Yup. Reinstalled the Catalyst driver via amd.com, and now it works again. I guess I'll just have to reinstall it every time I get a kernel update. Wohoo!

---

### Post by acesabe on 2010-03-17
sgfxi found package libgl1-mesa-glx needed upgrading before it re-installed the Ati fglrx module - perhaps ensuring this package is also upgraded before restarting will resolve this, although it can be expected that you need to reinstall a proprietary kernel module when a new kernel version gets installed.

---

