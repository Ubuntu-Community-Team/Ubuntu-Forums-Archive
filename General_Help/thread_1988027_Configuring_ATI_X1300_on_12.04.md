---
title: "Configuring ATI X1300 on 12.04"
date: 2012-05-26
forum: General Help
---

### Post by piriton on 2012-05-26
I am unable to get X working on 12.04.  I have an ATI X1300 video card and have the following configured in /etc/default/grub

 GRUB_GFXMODE=800x600
 GRUB_CMDLINE_LINUX_DEFAULT="915.modeset=0 nomodeset"

When I startup X, I don't see any graphical output.

When I run X -configure its unable to detect my graphics card.

Could some kind person post their xorg.conf or point me in the right direction,

---

### Post by piriton on 2012-06-01
****

[FONT=monospace]I didnt know that GRUB2 meant that I have to run the command below.  All works well.[/FONT]  
```
  update-grub

```

---

### Post by dino99 on 2012-06-01
you need to install & use xserver-xorg-video-radeon

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

open synaptic (install it in case) and:

-purge (complete removal) ALL the installed graphic drivers (remove xserver-xorg-video-all too , you dont need it)

- install xserver-xorg-video-radeon

close synaptic and open a  terminal to run:

sudo rm /etc/X11/xorg.conf

then log out/in and check the driver activation : sudo jockey-gtk

note: "915.modeset=0 nomodeset"
no need to enter the same setting twice (modeset=0 & nomodeset do the same job)

---

### Post by piriton on 2012-06-01
I dont have an /etc/X11/xorg.conf

The package xserver-xorg-video-radeon is installed.  I would prefer to leave all packages installed if possible.

How can I tell which modules X is using ?  The logfiles are confusing because there is so much information in there.  What should I be looking for in the logfiles ?

Is there an X tool to provide more verbose information about the current configuration before making extensive changes ?  i.e. I want to check to see if I am using the Radeon X driver or not, it's not clear to me right now.

```

# lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI M52 [Mobility Radeon X1300] [1002:7149]
# grep -i 10027149 /usr/share/xserver-xorg/pci/*.ids
# 

```

```

# dpkg --get-selections xserver-xorg-video-radeon
xserver-xorg-video-radeon            install

```

```

root@ubuntu:/var/log# grep LoadModule Xorg.0.log
[    44.247] (II) LoadModule: "extmod"
[    44.406] (II) LoadModule: "dbe"
[    44.449] (II) LoadModule: "glx"
[    44.496] (II) LoadModule: "record"
[    44.498] (II) LoadModule: "dri"
[    44.530] (II) LoadModule: "dri2"
[    44.532] (II) LoadModule: "fglrx"
[    45.436] (II) LoadModule: "fglrxdrm"
[    45.505] (II) LoadModule: "ati"
[    45.526] (II) LoadModule: "radeon"
[    45.612] (II) LoadModule: "vesa"
[    45.639] (II) LoadModule: "fbdev"
[    46.088] (II) LoadModule: "fbdevhw"
[    46.107] (II) LoadModule: "vgahw"
[    46.110] (II) LoadModule: "int10"
[    46.158] (II) LoadModule: "ddc"
[    46.158] (II) LoadModule: "i2c"
[    46.357] (II) LoadModule: "fb"
[    46.385] (II) LoadModule: "ramdac"
[    46.385] (II) LoadModule: "xaa"
[    47.415] (II) LoadModule: "evdev"
[    47.455] (II) LoadModule: "synaptics"

```What does the command failing below mean, that my current graphics driver does not support OpenGL ?

```

# fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

``````

# LIBGL_DEBUG=verbose glxinfo
name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

``````

# aticonfig
aticonfig: No supported adapters detected

```

---

### Post by piriton on 2012-06-03
Also why is xserver-xorg-video-radeon better than ATI's driver ?  Greatful for any advice, so that I can get have a faster X display.

---

### Post by Mark Phelps on 2012-06-03
> **piriton said:**
> Also why is xserver-xorg-video-radeon better than ATI's driver ?  Greatful for any advice, so that I can get have a faster X display.

The xorg-video-radeon drivers are the radeon open-source drivers. They are "better" in some respects than the restricted ATI drivers because they will work in situations where the ATI drivers will not.  

Most common example is if you are using a "legacy" video card (like yours) that will not run the current AMD drivers.

IF you were to force an installation of any ATI restricted drivers on your current system, when you rebooted, you would most likely see a corrupted display that would be useless.

Thus, in your situation, the open-source radeon drivers are the ones to use.

---

### Post by kkEspana on 2012-06-03
nothing else needs

---

### Post by piriton on 2012-06-03
Hi, thanks for the input.

How can I check that X is actually using the xorg-video-radeon driver?  Is there a tool which somehow queries the current running X config ?

The Xorg.0.log file is very confusing.  I understand that X chooses the most appropriate driver, however because fglxrinfo does not appear to work, I am not convinced that the xorg-video-radeon driver is being used, even though it's mentioned in the logfile along with numerous other drivers.

Was'nt there a tool called probe or something similar in Xfree86 3.x ?  Hang on, hav'nt we migrated from XFree86 to x.org now.  I am outta date.

I dont think that either avivotool or radeontool are useful in this case.

I am afraid to remove all of the other X drivers and completely mess up my X setup, beyond repair.  There must be another, easier method to do this ?

---

### Post by piriton on 2012-06-03
The solution ....

It seems that the fglrx driver prevented with the xorg-video-radeon driver because of an explicit kernel option to turn off the Radeon driver, to prevent a conflict.

I can now finally run glxgears and X is much faster with the Radeon driver.

```

# cat /etc/modprobe.d/fglrx.conf 

# This file was installed by fglrx
# Do not edit this file manually

blacklist radeon
alias fglrx fglrx
alias radeon off
alias lbm-radeon off


``````

apt-get remove fglrx fglrx-amdcccle

``````

 GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0"

```

---

