---
title: "No more GUI (X server) after updating 12.04, running on AMD Fusion (Radeon HD 6310)"
date: 2012-07-03
forum: General Help
---

### Post by Katchina on 2012-07-03
Hello,

My mother has a small AMD-fusion based desktop.  The integrated GPU is labelled as Radeon HD 6310.  I successfully made this machine work under 12.04 about 6-8 weeks ago.  If I remember properly, I did manually install AMD's binary driver.

On Sunday, while I was visiting, I did update the system, and now the GUI doesn't come up anymore at boot.  I haven't changed anything else.

Here's some basic info...

GPU (lspci | grep VGA) :
**00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]**

Kernel (uname -a) :
**3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux**

Latest Xorg log (cat /var/log/Xorg.0.log) :
**[http://paste.ubuntu.com/1072740]("http://paste.ubuntu.com/1072740")**

Running drivers (lsmod) :
**[http://paste.ubuntu.com/1072736]("http://paste.ubuntu.com/1072736")**

Also, running apt-get update and then apt-get upgrade didn't fix things, but it specifically says that the kernel packages (linux-generic, linux-headers-generic and linux-image-generic) are being kept as is (bare with me, this is a French system (yeah, remember, it's my mom's), it says "conservés" which I guess translates to "held back" i.e. not upgraded).

I'm a bit puzzled and don't know exactly where to go from here...
Can anyone help based on the info provided above ?
Thanks ahead for any hint.

---

### Post by mongolito404 on 2012-07-03
Did you try to reconfigure the xserver (but I'm not sure this has any use with recent Xorg server)?
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Katchina on 2012-07-07
Just tried dpkg-reconfigure xserver-xorg, but it's not helping a bit.
I've got no idea what to do from here on.
Anyone, any idea ?

---

### Post by msammels on 2012-07-07
Katchina, what exactly comes up? Do you get a text based interface? Anything?

---

### Post by Katchina on 2012-07-07
Not getting anything from the command.  Just a new CLI prompt after about 1/2 second or so...

---

### Post by Katchina on 2012-07-08
OK I did force upgrade the kernel from 3.2.0-24 to the following :
**3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux**

At boot, I now get a X server with a message stating :
[B]The system is running in low-graphics mode
Your screen, graphics card and input device settings could not be detected correctly.  You will need to configure these yourself.[/B]

After clicking the "OK" button (the only one that's available), I have to select one of these options :
[LIST]
[*]**Run in low-graphics mode for just one session.**  Running in low-graphics mode does not actually work (I only get a CLI prompt on tty1).
[*]**Reconfigure graphics.**  Reconfiguring graphics does not work either.  It asks me to make a decision between "Use default (generic) configuration" or "Use your backed-up configuration" but with either choice, after clikcing OK, I'm asked the same question again and again and again.
[*]**Troubleshoot the error.**  Troubleshooting the error gets me to a screen where I can view the xserver log file, the startup errors, and edit the configuration file.  Again, some of these options do not actually work, although I can have a look at the Xorg server log.
[*]**Exit to console login.**
[/LIST]

The new Xorg log file contains an interesting error message...

Complete log : **[http://paste.ubuntu.com/1080981/](http://paste.ubuntu.com/1080981/)**

Interesting lines :
```
[     5.574] (II) fglrx(0): Adapter AMD Radeon HD 6310 Graphics has 2 configurable heads and 1 displays connected.
[     5.574] (==) fglrx(0):  PseudoColor visuals disabled
[     5.574] (II) Loading sub module "ramdac"
[     5.574] (II) LoadModule: "ramdac"
[     5.574] (II) Module "ramdac" already built-in
[     5.574] (==) fglrx(0): NoDRI = NO
[     5.574] (==) fglrx(0): Capabilities: 0x00000000
[     5.574] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     5.574] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     5.574] (==) fglrx(0): UseFastTLS=0
[     5.575] (II) UnloadModule: "radeon"
[     5.575] (II) Unloading radeon
[     5.575] (II) UnloadModule: "vesa"
[     5.575] (II) Unloading vesa
[     5.575] (II) UnloadModule: "fbdev"
[     5.575] (II) Unloading fbdev
[     5.575] (II) UnloadModule: "fbdevhw"
[     5.575] (II) Unloading fbdevhw
[     5.575] (--) Depth 24 pixmap format is 32 bpp
[     5.575] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[     5.575] (WW) fglrx(0): ***********************************************************
[     5.575] (WW) fglrx(0): * DRI initialization failed                               *
[     5.575] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[     5.575] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[     5.575] (WW) fglrx(0): ***********************************************************
[     5.575] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
```

I don't really know where to go from here.  I have no idea how I should configure a modern Xorg server from the CLI, I haven't done anything like this in years.

Can anyone help ?

---

### Post by Katchina on 2012-07-08
Oh, also, here's my (fairly standard) xorg.conf file as of now :

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

(Or see it here : **[http://paste.ubuntu.com/1081028/](http://paste.ubuntu.com/1081028/)**)

---

### Post by Katchina on 2012-07-08
OK, problem solved, for the record :

* I had to uninstall the AMD/ATI driver (catalyst 12.4), using the --force option.
* I manually downloaded the new AMD/ATI catalyst 12.6 using wget.
* I installed the driver, which is now properly running (although constantly displaying the "AMD unsupported hardware" watermark, which as far as I remember was displayed only for a few seconds using the 12.4 drivers.

Frustrating thing is, I still don't know exactly what caused the problem in the first place, and whether it's going to happen again in the near future.

---

### Post by liju.g.chacko on 2012-07-28
I too had same experience. I had installed amd graphics driver from AMD site(amd-driver-installer-12.6-legacy-x86.x86_64). After upgrading kernel, gui desktop was not coming. It was showing "user 'motion' error". After reinstalling the graphics driver via command line, desktop was resumed.

*login to administrative user account
*type 'sudo -i' and enter password
*cd to the directory containing driver( amd-driver-installer-12.6-legacy-x86.x86_64.run file)
*Now type './amd-driver-installer-12.6-legacy-x86.x86_64.run  --install' <enter> and proceed.

---

### Post by liju.g.chacko on 2012-09-29
I have successfully installed graphics driver but by bluetooth is facing problem it is not identified in new kernel.

---

