---
title: "Xorg.conf problem"
date: 2012-07-30
forum: General Help
---

### Post by JCM_Pico on 2012-07-30
Hello there

I was trying to configure my Xorg.conf file using:
```
# Xorg -configure[CODE]

in order to be able to change my screen resolution

But I get this...

[CODE]X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
Current Operating System: Linux jcmteixeira-Linux 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=410badb1-efa5-42ab-b7a1-8387ec3dd2d2 ro quiet splash pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 vt.handoff=7
Build Date: 16 July 2012  08:06:31PM
xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 30 12:33:44 2012
List of video drivers:
	siliconmotion
	neomagic
	mach64
	nouveau
	mga
	sis
	savage
	sisusb
	trident
	qxl
	r128
	openchrome
	cirrus
	intel
	radeon
	s3
	ati
	vmware
	tdfx
	fbdev
	vesa
(++) Using config file: "/home/jcmteixeira/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.

```

Any help?

---

### Post by steeldriver on 2012-07-30
have you considered using xrandr instead of setting it through xorg.conf? 

[https://wiki.ubuntu.com/X/Config/Resolution/](https://wiki.ubuntu.com/X/Config/Resolution/)

I'm not much good with xorg.conf but if you want to pursue that route you should probably post the contents of your xorg.conf.new file so folks can take a look at it

---

### Post by Grenage on 2012-07-30
If you *want* to go down the xorg path, I have a guide [here]("http://www.grenage.com/xorg.html").

If you get stuck, post back with the relevant information, which would include:

Monitor make/model.
GFX model (lspci | grep VGA).
Desired resolution.

---

