---
title: "GUI Fails to start"
date: 2012-02-17
forum: General Help
---

### Post by Tweaker420 on 2012-02-17
Hello. When i boot up ubuntu 11.10 i am brought to only a text login screen and shell prompt. I did seek help on irc.freenode.net, i tried removing fglrx, rebooting, then re-installing it, still the same problem persists. The following is my /var/log/Xorg.0.log. Thank you in advance. I would have just attached the file but the attach button isn't working properlyat the moment. Thanks again!

[    31.019] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    31.019] X Protocol Version 11, Revision 0
[    31.019] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    31.019] Current Operating System: Linux AmigaBun2 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    31.019] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=6298e53f-c343-4a9c-8ae6-662e81f04745 ro quiet splash
[    31.019] Build Date: 19 October 2011  05:21:26AM
[    31.019] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    31.019] Current version of pixman: 0.22.2
[    31.019]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    31.019] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.019] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 17 21:00:52 2012
[    31.112] (==) Using config file: "/etc/X11/xorg.conf"
[    31.112] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.228] (==) ServerLayout "aticonfig Layout"
[    31.228] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    31.228] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    31.228] (**) |   |-->Device "aticonfig-Device[0]-0"
[    31.228] (==) Automatically adding devices
[    31.228] (==) Automatically enabling devices
[    31.384] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.384]     Entry deleted from font path.
[    31.384] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.384]     Entry deleted from font path.
[    31.384] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.384]     Entry deleted from font path.
[    31.411] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.411]     Entry deleted from font path.
[    31.412] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.412]     Entry deleted from font path.
[    31.533] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    31.533] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.533] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.533] (II) Loader magic: 0x7e0220
[    31.533] (II) Module ABI versions:
[    31.533]     X.Org ANSI C Emulation: 0.4
[    31.533]     X.Org Video Driver: 10.0
[    31.534]     X.Org XInput driver : 12.3
[    31.534]     X.Org Server Extension : 5.0
[    31.534] (--) PCI:*(0:1:0:0) 1002:6759:1092:6570 rev 0, Mem @ 0xd0000000/268435456, 0xfe9e0000/131072, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[    31.534] (II) Open ACPI successful (/var/run/acpid.socket)
[    31.534] (II) "extmod" will be loaded by default.
[    31.534] (II) "dbe" will be loaded by default.
[    31.534] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    31.534] (II) "record" will be loaded by default.
[    31.534] (II) "dri" will be loaded by default.
[    31.534] (II) "dri2" will be loaded by default.
[    31.534] (II) LoadModule: "glx"
[    31.790] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    32.210] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    32.211]     compiled for 6.9.0, module version = 1.0.0
[    32.211] (II) Loading extension GLX
[    32.211] (II) LoadModule: "extmod"
[    32.257] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    32.268] (II) Module extmod: vendor="X.Org Foundation"
[    32.268]     compiled for 1.10.4, module version = 1.0.0
[    32.268]     Module class: X.Org Server Extension
[    32.268]     ABI class: X.Org Server Extension, version 5.0
[    32.268] (II) Loading extension MIT-SCREEN-SAVER
[    32.268] (II) Loading extension XFree86-VidModeExtension
[    32.268] (II) Loading extension XFree86-DGA
[    32.268] (II) Loading extension DPMS
[    32.268] (II) Loading extension XVideo
[    32.268] (II) Loading extension XVideo-MotionCompensation
[    32.268] (II) Loading extension X-Resource
[    32.268] (II) LoadModule: "dbe"
[    32.269] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    32.276] (II) Module dbe: vendor="X.Org Foundation"
[    32.276]     compiled for 1.10.4, module version = 1.0.0
[    32.276]     Module class: X.Org Server Extension
[    32.276]     ABI class: X.Org Server Extension, version 5.0
[    32.276] (II) Loading extension DOUBLE-BUFFER
[    32.276] (II) LoadModule: "record"
[    32.276] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    32.277] (II) Module record: vendor="X.Org Foundation"
[    32.277]     compiled for 1.10.4, module version = 1.13.0
[    32.277]     Module class: X.Org Server Extension
[    32.277]     ABI class: X.Org Server Extension, version 5.0
[    32.277] (II) Loading extension RECORD
[    32.277] (II) LoadModule: "dri"
[    32.277] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    32.299] (II) Module dri: vendor="X.Org Foundation"
[    32.299]     compiled for 1.10.4, module version = 1.0.0
[    32.299]     ABI class: X.Org Server Extension, version 5.0
[    32.299] (II) Loading extension XFree86-DRI
[    32.299] (II) LoadModule: "dri2"
[    32.299] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    32.300] (II) Module dri2: vendor="X.Org Foundation"
[    32.300]     compiled for 1.10.4, module version = 1.2.0
[    32.300]     ABI class: X.Org Server Extension, version 5.0
[    32.300] (II) Loading extension DRI2
[    32.300] (II) LoadModule: "fglrx"
[    32.300] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    32.848] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    32.875]     compiled for 1.4.99.906, module version = 8.88.7
[    32.875]     Module class: X.Org Video Driver
[    32.884] (II) Loading sub module "fglrxdrm"
[    32.884] (II) LoadModule: "fglrxdrm"
[    32.884] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    33.029] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    33.029]     compiled for 1.4.99.906, module version = 8.88.7
[    33.029] (II) ATI Proprietary Linux Driver Version Identifier:8.88.7
[    33.029] (II) ATI Proprietary Linux Driver Release Identifier: 8.881                                
[    33.029] (II) ATI Proprietary Linux Driver Build Date: Jul 28 2011 17:04:01
[    33.029] (++) using VT number 7

[    33.030] (WW) Falling back to old probe method for fglrx
[    33.145] (II) PCS database file /etc/ati/amdpcsdb not found
[    33.145] (II)   Creating PCS database from initial defaults instead
[    33.162] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found
[    33.162] (EE) No devices detected.
[    33.162] 
Fatal server error:
[    33.162] no screens found
[    33.162] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    33.162] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    33.162]

---

### Post by Bucky Ball on 2012-02-17
Try:

```
sudo startx
```

What happens?

---

### Post by Tweaker420 on 2012-02-17
Thanks for replying. I tried that just now, although i couldn't figure out how to cut and paste all of it with command line only or scroll up (my own ignorance no doubt) i typed what i could see on the screen at the end when the command failed, as follows.

(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found
(EE) No devices detected.

Fatal Server error:
no screens found

 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: connection refused
xinit: server error
tweak@AmigaBun2:~$


Thanks!

---

