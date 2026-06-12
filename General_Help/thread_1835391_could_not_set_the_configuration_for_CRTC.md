---
title: "could not set the configuration for CRTC"
date: 2011-08-29
forum: General Help
---

### Post by azen0r on 2011-08-29
Hi,

I've a computer running with natty 11.04 but instead of kernel 2.6.38-10 I need to use a vanilla kernel 2.6.32.11

With 2.6.38-10, I have no problem with display, various resolutions are proposed and supported. I can choose any of them.
In this configuration, xrandr returns : 

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
```However, when I'm using vanilla kernel 2.6.32.11, my monitor is not recognized and available resolutions are limited to unpleasant ones :

```
$ xrandr 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0 
```I tried to force the resolution to 1280*1024 :

```
$ cvt 1280 1024 60
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

$ xrandr  --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr: Failed to get size of gamma for output default

$ xrandr --addmode default 1280x1024_60.00
xrandr: Failed to get size of gamma for output default
```1280*1024 resolution is then available in the configuration window but when I select it, I get the following message :

```
could not set the configuration for CRTC 262
```Does any of you know what changes between natty kernels 2.6.38-10 and vanilla kernel 2.6.32.11 ?

Thank you.

---

### Post by realzippy on 2011-08-29
Do you use integrated graphics core from Intel I3/5/7 CPU ?
Why do you need to use a vanilla kernel 2.6.32.11 ?

---

### Post by gordintoronto on 2011-08-29
What video adapter? What monitor?

---

### Post by azen0r on 2011-08-30
[QUOTE=realzippy]Do you use integrated graphics core from Intel I3/5/7 CPU ?[/QUOTE]
I don't know how to answer this question, how to tell ?
EDIT : Uh, Doesn't the following answer yes to that question ?

I need this kernel because I then patch it to make it a real time linux. But the problem I describe also occurs on unpatched version.

My monitor is an LCD from Samsung

As for my video adapter, lshw tells 
```
description : VGA compatible controller
product : 4 series chipset integrated graphics controller
vendor : Intel Corporation
...
```Please tell me if you need more information

Do you think it would be usefull to force generation of a xorg.conf with the kernel that is ok and then force other kernel to use it ?

---

### Post by realzippy on 2011-08-30
```
product : 4 series chipset integrated graphics controller
```

..is not a cpu-integrated graphics core as in the I3/5/7 CPUs.
For those you would have needed at least kernel 2.6.38...

Forcing and chanching xorg.conf won't work,remember xrandr reported:

```
$ xrandr 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, [COLOR="Red"]maximum 1024 x 768[/COLOR]
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0
```

That  why creating/adding higher resolution modes did not work...

From **[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)**:

On the other hand, the -realtime kernel is a PREEMPT_RT patched kernel based on the vanilla source tree (not the Ubuntu source). This kernel will be missing Ubuntu specific code, patches or security fixes and it isn't guaranteed to be compatible with any external software (low level utilities, **DKMS drivers** and so on). 

...guess that's why your intel kernel module doesn't get loaded,but you say it also occurs on unpatched version (?)..
What is output from:
```
lshw -c video
``` (whole output please..)
when running vanilla kernel?

---

### Post by azen0r on 2011-08-30
Here is lshw output when running on unmodified vanilla 2.6.32.11 kernel (except I added support of ext4) :
```
~$ sudo lshw -C video
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fe400000-fe7fffff memory:d0000000-dfffffff(prefetchable) ioport:dc00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe900000-fe9fffff

```

---

### Post by realzippy on 2011-08-30
so intel driver is not working,otherwise there would be
driver=intel in
configuration: latency=0
like eg, here:
configuration: driver=i915 latency=0

.............................
You might try (not much hope) kinda vanilla xorg.conf:

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        HorizSync       28.0 - 70.0
        VertRefresh     56.0 - 75.0
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes        "1280x1024" "1024x768"
	EndSubSection
EndSection

```

...assuming you know what to do if that xorg.conf fails to start X
(since we are not in beginner's talk)

If it boots,what does xrandr -q say?

---

### Post by azen0r on 2011-08-30
So I copied your code in /etc/X11/xorg.conf (created the file since there was none)
It fails to boot on vanilla kernel. In recovery mode, it hangs after printing "loading initial ramdisk..."

But it still boots on natty kernel...

---

### Post by realzippy on 2011-08-30
You could try "vesa" instead of intel in device section.

---

### Post by azen0r on 2011-08-30
GREAT !
It did the trick and I'm gratefull for that, so thanks a lot=D>

Thank you also for explaining how you think and why some of my ideas were hopeless. I can't say I'm a pro but I feel I understand my problem better.

---

### Post by realzippy on 2011-08-30
Admit I do not understand why it did not work without any xorg.conf,
since vesa driver should kick in if there is no intel module to load.
Did you recompile the kernel?

---

### Post by azen0r on 2011-08-31
Yes I recompiled the kernel at install.
Main steps I followed are :
```
$ sudo git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-2.6.32.y.git
$ sudo make menuconfig
$ sudo cp ./arch/x86/configs/i386_defconfig .config
$ sudo apt-get install kernel-package
$ cd /usr/src/linux-2.6.32.y
$ sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
$ cd /usr/src/
$ sudo dpkg -i linux-headers-2.6.32.11-custom_2.6.32.11-custom-10.00.Custom_i386.deb
$ sudo dpkg -i linux-image-2.6.32.11-custom_2.6.32.11-custom-10.00.Custom_i386.deb
$ sudo update-initramfs -c -k 2.6.32.11-custom
```
Hope it will help you understand.

---

