---
title: "Dual monitor Intel + Nvidia VGA"
date: 2012-07-13
forum: General Help
---

### Post by Josie86 on 2012-07-13
Hi guys,
I've read like thousands of post about this issue before posting, but I really can't get to make my dual monitor setup to work.

I've got an external VGA card (Geforce 6500) and an internal VGA card and I can see both of them with the lspci command:

```
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
    Subsystem: ASRock Incorporation Device 29c2
    Kernel driver in use: i915
    Kernel modules: i915
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
--
04:00.0 VGA compatible controller: NVIDIA Corporation NV44 [GeForce 6500] (rev a1)
    Kernel driver in use: nouveau
    Kernel modules: nvidia_current, nvidia, nouveau, nvidiafb
```

But xrandr -q gives me just one screen and, in fact, the other one is black
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1024x768       70.1*+   60.0  
   1920x1080      60.0 +
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1
```

I've tried MANY xorg.conf configurations, this is the last one I came up with but I'm not an expert (not at all..) so it's like a copy and paste I've made from various forums :(

```


Section "Device"
    Identifier "Device0"
    Driver "intel"
    BusID "PCI:00:02:0"
EndSection


Section "Device"
    Identifier "Device1"
   Driver      "nvidia"
   VendorName  "nVidia Corporation"
   BoardName   "NV44 [GeForce 6500]"
    BusID "PCI:04:00:0"
EndSection

Section "Monitor"
   Identifier  "Monitor0"
   HorizSync   30-94
   VertRefresh 48-85
EndSection

Section "Monitor"
   Identifier  "Monitor1"
   HorizSync   30-94
   VertRefresh 48-85
EndSection

Section "Screen"
   Identifier  "Screen0"
   Device      "Device0"
   Monitor     "Monitor0"
   DefaultDepth    24
   SubSection "Display"
       Depth       24
       Modes       "1024x768"
   EndSubSection
EndSection

Section "Screen"
   Identifier  "Screen1"
   Device      "Device1"
   Monitor     "Monitor1"
   DefaultDepth    24
   SubSection "Display"
       Depth       24
       Modes       "1920x1080"
   EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen  0   "Screen0" Absolute 0 180 
    Screen  1   "Screen1" Absolute 1600 0
EndSection

```

The result of this stuff is that I'm using just one monitor (the other one is black) at a very strange resolution.
By editing the xorg.conf I've been able to make the other monitor work (the nvidia card one), but then the other got black..

---

### Post by Josie86 on 2012-07-16
Anyone? :(

---

### Post by NikTh on 2012-07-16
Hi , 
i think you must install nvidia additional drivers to do this job (dual-monitor)
Open a terminal and install newer nvidia drivers by adding a repository . 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get install nvidia-current
```After installation finish create a new xorg file with this command 
```
sudo nvidia-xconfig
```Reboot your system . 
Then open nvidia settings and try to enable dual monitor feature. 
Thanks

---

### Post by Josie86 on 2012-07-16
I've done that but unfortunately the nvidia settings tools always tells me I'm not using the driver

---

### Post by dargaud on 2012-07-16
Then maybe you have the 'nouveau' driver. I've had problems on one of my systems where I had to disable it.
Another option is to go on nVidia'a website, download and manually install their driver (Ctrl-Alt-F2, kill kdm, etc)

---

### Post by NikTh on 2012-07-16
> **dargaud said:**
> Then maybe you have the 'nouveau' driver. I've had problems on one of my systems where I had to disable it.
Another option is to go on nVidia'a website, download and manually install their driver (Ctrl-Alt-F2, kill kdm, etc)
Hi ,
Nouveau driver **must be** blacklisted automatically , when nvidia driver installed. I don't know if this is a bug or something .

I count to Bios. 
@Josie86 , try to boot in to Bios configuration and see if you can disable the integrated intel graphics . 
And for what release of Ubuntu we speak ? 12.04 ? 
Thanks.

---

### Post by 3Miro on 2012-07-16
Check your BIOS settings and disable the integrated video card. It is highly recommended that you do that since you cannot have two different video cards when using the Nvidia driver.

Install the Nvidia driver and use the Nvidia-Settings tool to set the two monitors. Note that both monitors must be connected to the Nvidia video card.

For your current Xorg, I am surprised that you can even boot with the two video cards declared. One of them is being ignored (probably the Nvidia one since Nvidia settings doesn't detect the driver). Nvidia doesn't support hybrid graphics for Linux and hence their driver will not work if both Nvidia and Intel video cards are enabled. Noveau might work, but it is generally weak and I don't think it will work well on an old card. The odds of Noveau working are slim.

---

