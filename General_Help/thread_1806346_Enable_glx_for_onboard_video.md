---
title: "Enable glx for onboard video?"
date: 2011-07-17
forum: General Help
---

### Post by doriad on 2011-07-17
I had an NVidia card with NVidia drivers installed. Then I removed the card and am now using my motherboard onboard video. Everything seemed to be working fine, but with a few programs I get errors like
```

gl~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

The only thing I could find online is to set the right driver in xorg.conf, but first, I don't have an /etc/X11/xorg.conf, and second, what would I set it to (all of the tutorials seem to be for nvidia)? Is there any way I can get this glx extension working with this non-nvidia card?

Thanks,

David

---

### Post by doriad on 2011-07-25
Any clues? I tried reinstalling libgl1-mesa-glx with:

dpkg -r --force-depends libgl1-mesa-glx
apt-get install libgl1-mesa-glx

but it didn't seem to change anything.

David

---

### Post by Kira_Belka on 2011-07-25
Firstly lspci plz..so what's model of onboard card?
if it's not nvidia.. 
then I suppose you have to purge nvidia drivers
And to reinstsall xorg-video-all driver

---

### Post by doriad on 2011-07-25
```
~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

How do I reinstall xorg-video-all? I tried this:
```

~$ sudo apt-get install xorg-video-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xorg-video-all

```

Thanks for your reply so far!

David

---

### Post by Kira_Belka on 2011-07-25
> **doriad said:**
> ```
~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

How do I reinstall xorg-video-all? I tried this:
```

~$ sudo apt-get install xorg-video-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xorg-video-all

```

Thanks for your reply so far!

David
awfully sorry I'm blondie :)) xserver-xorg-video-all

and intel IGMA31 card... mmmm.. so xserver-xorg-video-intel driver

---

### Post by doriad on 2011-07-25
Hm, it seems like I already have those installed?

```
~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libaudio-dev libopenjpeg2 mesa-common-dev qt3-dev-tools libosmesa6
  libdrm-dev liblcms1-dev libkms1 libmng-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


~$ sudo apt-get install xserver-xorg-video-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-all is already the newest version.
The following packages were automatically installed and are no longer required:
  libaudio-dev libopenjpeg2 mesa-common-dev qt3-dev-tools libosmesa6
  libdrm-dev liblcms1-dev libkms1 libmng-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

---

### Post by Kira_Belka on 2011-07-25
> **doriad said:**
> Hm, it seems like I already have those installed?

```
~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libaudio-dev libopenjpeg2 mesa-common-dev qt3-dev-tools libosmesa6
  libdrm-dev liblcms1-dev libkms1 libmng-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


~$ sudo apt-get install xserver-xorg-video-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-all is already the newest version.
The following packages were automatically installed and are no longer required:
  libaudio-dev libopenjpeg2 mesa-common-dev qt3-dev-tools libosmesa6
  libdrm-dev liblcms1-dev libkms1 libmng-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

I mean purge nvidia driver and reinstall xserv-xorg-video-all )

---

### Post by doriad on 2011-07-25
What do you mean "purge"? Do you have a command for me to run :) ?

Also, how do I "reinstall"? Uninstall + install? Like this:

```
dpkg -r xserver-xorg-video-all
apt-get install xserver-xorg-video-all
```
?

David

---

### Post by Kira_Belka on 2011-07-25
> **doriad said:**
> What do you mean "purge"? Do you have a command for me to run :) ?

Also, how do I "reinstall"? Uninstall + install? Like this:

```
dpkg -r xserver-xorg-video-all
apt-get install xserver-xorg-video-all
```
?

David

apt-get purge "bla-bla-bla name of package" :)) and yep purge and install again ( I mean "reinstall" in my understanding :)))

---

### Post by doriad on 2011-07-25
Awesome!! This did the trick:

```
apt-get purge nvidia-common* nvidia-current* nvidia-settings*
apt-get purge xserver-xorg-video-intel
apt-get install xserver-xorg-video-intel
```

Thanks so much!

David

---

