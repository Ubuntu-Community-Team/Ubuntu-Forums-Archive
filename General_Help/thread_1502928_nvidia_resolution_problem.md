---
title: "nvidia resolution problem"
date: 2010-06-06
forum: General Help
---

### Post by knights_templar on 2010-06-06
Hi all

Have used Ubuntu or derivative for years, and have generally found answers by a little detective work, this one is defeating me, so can anyone out there help ????

I upgraded to Mint 9, Lucid based, and installed the Nvidia drivers, after a little stress I have the following,

system boots to login
screen resolutions are correct
login
resolution switches to low

a search of the log appear to show that at the last minuet nvidia is switching the lower mode, and I cant find out why, any ideas ?

I have attached xorg.conf and xorg log, the last entry is me switching to a higher res in nvidia settings

regards

---

### Post by rplantz on 2010-06-07
I'm getting the same thing. It only happens about 25% of the time.

My xorg.conf file is essentially the same as knights_templar's.

Here is what looks like the significant part of my log file when it went into low res mode:
```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Fri Mar 12 00:38:50 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1280x1024_85 +0+0; nvidia-auto-select +0+0"
(**) Jun 07 06:51:21 NVIDIA(0): Enabling RENDER acceleration
(II) Jun 07 06:51:21 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 07 06:51:21 NVIDIA(0):     enabled.
(EE) Jun 07 06:51:21 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Jun 07 06:51:21 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Jun 07 06:51:21 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

```
I continued into terminal mode, logged in, did a startx, and things were okay. I rebooted, and all was fine --- for this session. But this has been going on for about a week now. My next reboot could send me back into low res mode.

---

