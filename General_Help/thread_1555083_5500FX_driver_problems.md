---
title: "5500FX driver problems"
date: 2010-08-17
forum: General Help
---

### Post by andy_blah on 2010-08-17
I've just bought a new GeForce FX5500 card and I seem to have problems with it in Ubuntu. At first I tried to go to System->Administration->HardWare drivers to look for a driver for the card and enable it. After it searched for one it returned none saying that there are no proprietary drivers are in use. After that I've tried to install the nVidia driver manually from their site and it all went well, did a restart only to notice that the driver doesn't work. When I try to access the nVidia settings panel it says: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server." Doing what I was instructed in that message returns this: 
```
WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

```

After that I took a look at the Hardware Drivers window the NVidia driver shows up but it says that it isn't used, so I deactivate it and reactivate it and do a restart. After that Ubuntu greets me with this message:

```
Ubuntu now operates in safe mode, the following error occured:
(EE) NVIDIA :Failed to load the NVIDA kernel module. Please check your (blank space, nothing is written after this)
(EE) NVIDIA : (blank space, again) system's kernel log for additional messages
(EE) failed to laod module "nvidia" (module specific error, 0)
(EE) No drivers available
```

```
~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

```

---

### Post by andy_blah on 2010-08-18
*bump* Nobody knows?

---

### Post by Ad@m on 2010-08-18
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Did you follow the above?

---

### Post by andy_blah on 2010-08-18
No, I didn't do so, but started doing it now. Apparently /etc/default/linux-restricted-modules-common doesn't exist in my Ubuntu install plus the xorg.conf file doesn&#539;t have any ”Modules” section so I stopped following the guide for now because I don&#539;t want to do something stupid XD.

---

### Post by andy_blah on 2010-08-18
After no replies I went on to continue with the guide, but I found out that it was for an older version of Ubuntu, most of the commands in the driver installation process aren't valid for Karmic

---

### Post by LowSky on 2010-08-18
```
sudo apt-get install nvidia-173

sudo update-alternatives --config gl_conf

sudo ldconfig

sudo nvidia-xconfig

sudo reboot
```
you may also have to uninstall the nouveau driver

---

### Post by andy_blah on 2010-08-18
Unfortunately that doesn't change anything so it is either the above commands aren't the solution, or I didn't do it properly.

”you may also have to uninstall the nouveau driver” -> Not sure what you mean by that

”sudo update-alternatives --config gl_conf” -: This line has shown me a list with a few options, I pressed enter and went on with what was previously set because I have no idea what those mean.

---

### Post by andy_blah on 2010-08-19
*bump* I urgently need to get this fixed...

---

### Post by realzippy on 2010-08-19
```
WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'
```

*"After that I took a look at the Hardware Drivers window the NVidia driver shows up but it says that it isn't used, so I [COLOR="Red"]deactivate it and reactivate[/COLOR] it and do a restart. After that Ubuntu greets ...."*


After that -I think - you should have restarted and everything would have been o.k.


Would suggest to add this ppa to your sources

[ppa:ubuntu-x-swat/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

and install Alberto Milone's nvidia 173.xx driver -hopefully- with

Administration/Hardwaredrivers tool.. no need to [disable nouveau manually]("http://ubuntuforums.org/showpost.php?p=9203671&postcount=1").

---

### Post by andy_blah on 2010-08-19
Thank you very much! The last link you suggested worked perfectly, so I'll mark the thread as solved~ \^o^/

---

