---
title: "sudo X -configure gives error"
date: 2012-04-28
forum: General Help
---

### Post by DavidSommen on 2012-04-28
Following to this thread: ([http://ubuntuforums.org/showthread.php?t=1965131&page=2](http://ubuntuforums.org/showthread.php?t=1965131&page=2)), which has been closed (I think because the release of Precise), I tried to do sudo X-configure to create a xorg.conf.new.

This is the output from the terminal:
```


X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
Current Operating System: Linux sommen 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=af8d32b1-4fdd-4f02-b16c-5ab13ff5fece ro quiet splash radeon.audio=1 vt.handoff=7
Build Date: 20 April 2012  05:12:02AM
xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 28 15:12:02 2012
List of video drivers:
	radeon
	ati
	r128
	cirrus
	intel
	vmware
	nouveau
	siliconmotion
	sis
	savage
	sisusb
	mach64
	trident
	openchrome
	neomagic
	qxl
	s3
	mga
	tdfx
	fbdev
	vesa
(++) Using config file: "/home/sommen/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting.
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.

```

Is this normal? If not, does it have to anything with my previous problem (Video tearing on my hdmi out) or not at all?

Thanks for the help.

---

