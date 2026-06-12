---
title: "VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro] with Jaunty"
date: 2009-09-07
forum: General Help
---

### Post by tons2000 on 2009-09-07
I've been trying to enable hardware accelerated graphics on the Ebox 4800 containing VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro] as graphics chip.

I installed the driver for Ubuntu 9.04 from [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) by following the instructions in the readme.

However I cant seem to enable hardware accellerated graphics.

I've attached my xorg.conf and Xorg.0.log and lspci.txt and I assume the lines

```

(EE) AIGLX error: dlopen of /usr/lib/dri/via_unichrome_dri.so failed (/usr/lib/dri/via_unichrome_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering

```are the reason for this not working.

Ofcourse I tried to search for via_unichrome_dri.so but without finding it.

The binary driver package for older versions of ubuntu contains this file however simply copying it doesnt help.


./compiz-check returns

```

snot@snot-desktop:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro] (rev 03)
 Driver in use:         via
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```Any help appreciated, thanks in advance


Seb

---

