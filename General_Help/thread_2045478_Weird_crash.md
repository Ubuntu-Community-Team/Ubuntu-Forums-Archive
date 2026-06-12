---
title: "Weird crash"
date: 2012-08-21
forum: General Help
---

### Post by TangoSF on 2012-08-21
Here's the problem:
The Xubuntu (12.04) running on  my laptop (Thinkpad T430) crash randomly, when it crashes, nothing works, Ctrl + Alt + F1~F6 fails too. I have to cut the power and reboot. I think it might be some problems with X server, but I'm not sure. Here's some log file fragment that I find in /var/log/Xorg.1.org:


[  3069.998] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[  3069.998] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  3069.999] (II) [KMS] Kernel modesetting enabled.
[  3069.999] (WW) Falling back to old probe method for vesa
[  3069.999] (WW) Falling back to old probe method for fbdev
[  3069.999] (II) Loading sub module "fbdevhw"
[  3069.999] (II) LoadModule: "fbdevhw"
[  3069.999] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3069.999] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3069.999] 	compiled for 1.11.3, module version = 0.0.2
[  3069.999] 	ABI class: X.Org Video Driver, version 11.0
[  3069.999] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  3069.999] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  3069.999] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  3069.999] (==) RADEON(0): Default visual is TrueColor
[  3069.999] (==) RADEON(0): RGB weight 888
[  3069.999] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  3069.999] (--) RADEON(0): Chipset: "ATI Radeon HD 4350" (ChipID = 0x954f)
[  3069.999] (II) RADEON(0): PCIE card detected
[  3069.999] drmOpenDevice: node name is /dev/dri/card0
[  3069.999] drmOpenDevice: open result is 9, (OK)
[  3069.999] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  3069.999] drmOpenDevice: node name is /dev/dri/card0
[  3069.999] drmOpenDevice: open result is 9, (OK)
[  3069.999] drmOpenByBusid: drmOpenMinor returns 9
[  3069.999] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  3069.999] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  3069.999] (EE) RADEON(0): [drm] failed to set drm interface version.
[  3069.999] (EE) RADEON(0): Kernel modesetting setup failed
[  3069.999] (II) UnloadModule: "radeon"
[  3069.999] (II) Unloading radeon
[  3069.999] (EE) Screen(s) found, but none have a usable configuration.
[  3069.999] 
Fatal server error:
[  3069.999] no screens found
[  3069.999] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  3069.999] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[  3070.000] 
[  3070.007]  ddxSigGiveUp: Closing log
[  3070.007] Server terminated with error (1). Closing log file.


A lots of things faild, like:
RADEON(0): [drm] failed to set drm interface version.
RADEON(0): Kernel modesetting setup failed
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error: no screens found
Server terminated with error (1). Closing log file.

So, can you guys help me to find out what can be the problem? Random crashes are really annoying. Thanks.

---

