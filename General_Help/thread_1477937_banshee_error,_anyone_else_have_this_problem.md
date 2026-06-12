---
title: "banshee error, anyone else have this problem?"
date: 2010-05-09
forum: General Help
---

### Post by sdowney717 on 2010-05-09
simply this. View a video podcast, then while watching it click on another video podcast
The screen goes black with just the cover art showing
To get video back, you have to kill it and start over

I think this is the line showing the trouble
[Warn 07:56:18.288] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0

> [Info  07:56:05.679] Running Banshee 1.7.0: [Ubuntu 10.04 LTS (linux-gnu, i486) @ 2010-05-08 01:11:57 UTC]
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:85: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:89: Murrine configuration option "gradients" is no longer supported and will be ignored.
[Info  07:56:06.552] All services are started 0.722378
[Info  07:56:07.060] nereid Client Started
[Warn  07:56:07.229] Caught an exception - System.Exception: org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at Hal.IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 
[Warn  07:56:18.288] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
scott@scott-desktop:~$ 


---

