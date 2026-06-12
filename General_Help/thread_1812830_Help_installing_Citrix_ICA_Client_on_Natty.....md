---
title: "Help installing Citrix ICA Client on Natty...."
date: 2011-07-26
forum: General Help
---

### Post by kromix on 2011-07-26
Older versions of instructions on how to get this to work seems to not work on Natty...

Installed citrix, got it under Applications, but my issue is:

kromix@KroLaptop:/usr/lib32$ ldd /usr/lib/ICAClient/wfcmgr
	linux-gate.so.1 =>  (0xf76ec000)
	**libXm.so.4 => not found**
	libXp.so.6 => /usr/lib32/libXp.so.6 (0xf76c1000)
	libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf76b0000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf76a8000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7690000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7679000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7675000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7671000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7658000)
	libc.so.6 => /lib32/libc.so.6 (0xf74fb000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf74a9000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf738d000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf737e000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf737a000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf7375000)
	/lib/ld-linux.so.2 (0xf76ed000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf735c000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7355000)

sudo apt-get install libmotif3 gets me 

Package libmotif3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmotif4

E: Package 'libmotif3' has no installation candidate


This is my next step but I can't get it installed, what else can I try?

---

### Post by toddyfranz on 2011-08-01
Hi.

> **kromix said:**
> 
  libmotif4

This is my next step but I can't get it installed, what else can I try?

You can install the libmotif4 Package with "sudo apt-get install libmotif4" . Than you get libXm.so.4. See [filelist]("http://ns2.canonical.com/natty/all/libmotif4/filelist").

Regards,
Torsten

---

### Post by odinb on 2011-09-01
Did you get it working?

If not, try this: [http://ubuntuforums.org/showthread.php?t=1837254](http://ubuntuforums.org/showthread.php?t=1837254)

---

