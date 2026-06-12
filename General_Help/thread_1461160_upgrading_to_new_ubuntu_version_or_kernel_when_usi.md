---
title: "upgrading to new ubuntu version or kernel when using latest nvidia driver"
date: 2010-04-23
forum: General Help
---

### Post by tchoper on 2010-04-23
I installed the latest NVIDIA driver (newer than the one that comes with the restricted drivers packages). Will having this newer driver cause me any problems when I upgrade Ubuntu or the kernel? I've heard that using a driver that's not part of the Ubuntu package can cause problems and has to be uninstalled before upgrading - is this still true? Thanks.

---

### Post by klemes on 2010-04-24
Yes in fact every time that you upgrade the kernel the nvidia kernel module must be rebuild through running the installation package coming from nvidia again.
Prior to upgrade it would be wise to change temporarily to the nv (open source) driver and then carry on with the upgrade.If you want after the upgrade to use the proprietary drivers from nvidia then you will have to run the installer again  as you must do so after every kernel upgrade.

---

### Post by tchoper on 2010-04-24
Do you mean the restricted driver that is accessible through preferences -> administration?  And if so, how do I get that back?

---

### Post by gradinaruvasile on 2010-04-24
DO NOT mix the driver from the nvidia site (the .run file) with the ubuntu-provided driver!

Use either one - NEVER install both. If you want to uninstall the .run driver, stop X/gdm, and start the driver with --uninstall:

/path/drivername.run --uninstall

This will remove the driver. Also remove/rename /etc/X11/xorg.conf. On the next X start the nv driver will be used and you may install the ubuntu-provided driver - although sometimes it dissapears from the hardware drivers section, the package can be installed (the name is nvidia-glx or something similar).

Other than that, i use these drivers since Ubuntu 7.10 (8.04/8.10/9.04/9.10 and now Debian Squeeze) and they are really stable. Kernel updates only happen now and then and you have to reboot anyway to use them - just start in single-user mode (recovery), install the driver, press ctrl-d (thats logout), and gdm will load.

But there is 2 more subtle thingies:

The xorg (or some of its components) updates may bork the nvidia driver files too.
It happened to me on Debian Squeeze to have glx killed by xorg updates (driver reinstall solved it), but here are frequent updates to every system component, including xorg - on Ubuntu's stable versions it never happened to me.

Also, in Ubuntu installing the ppa for mplayer with vdpau may kill vdpau support because it installs a package (libvdpau something) that overwrites the nvidia driver's vdpau libraries. So if this is the case, install the ppa, install/upgrade mplayer than reinstall the driver (and watch out for subsequent upgrades).

These things may happen if you are using the nvidia-provided driver.

---

### Post by 3rdalbum on 2010-04-24
There is a method to register the Nvidia driver with DKMS, so the driver will be rebuilt automatically every time the kernel updates. There should be a HOWTO floating around for it. However, I've been too lazy to do this and now I have to rebuild the driver every time the kernel updates.

When you boot up with a driver that's too old for the kernel, Ubuntu asks you what you want to do; just choose Run a Terminal (or whatever the entry is) and you'll be able to reinstall the driver from there.

For the record, I manually installed the driver because when I installed Lucid it still had the older Nvidia driver, the one with the fan speed problems.

---

### Post by tchoper on 2010-04-26
Thank you all for the informative answers.  I was initially having trouble removing the driver; this was, as gradinaruvasile pointed out, due to having both the restricted driver and proprietary driver installed simultaneously.  I removed the restricted and was then able to easily uninstall.  Thanks!

---

