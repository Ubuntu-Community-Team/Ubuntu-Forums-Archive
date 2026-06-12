---
title: "Second monitor not detected"
date: 2011-09-04
forum: General Help
---

### Post by ConceitedCode on 2011-09-04
I just added a Radeon HD 6570 video card to my desktop computer. It is running 11.04 64bit. I have 2 monitors that I am trying to use, but it can only detect the monitor plugged into the vga port. Both monitors are vga and I am using a dvi to vga adapter that I know works. I installed the fglrx driver. No matter what I try the monitor in the dvi port using the adapter is not detected. Any ideas?

---

### Post by Vakman on 2011-09-04
Please try this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo aticonfig --initial
sudo aticonfig --initial=dual-head --screen-layout=left
```
If this does not work let me know, after this restart X by pressing Ctrl + Alt +Backspace.

Also, please post the output of:
```
fglrxinfo
```

---

### Post by ConceitedCode on 2011-09-04
I tried `sudo aticonfig --initial` and got this

```
Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0

```

The output of fglrxinfo is

```
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6500 Series
OpenGL version string: 4.1.10665 Compatibility Profile Context
```

Here is the original xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

```

---

### Post by Vakman on 2011-09-04
Did you install the drivers via Hardware Drivers in Ubuntu or did you install manually?

Also try running the second part of the aticonfig command anyway, the one I sent last time below ```
sudo aticonfig --initial=dual-head --screen-layout=left
```and then also this:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

---

### Post by ConceitedCode on 2011-09-04
I used Hardware Drivers.

the second command show this.

```
Found fglrx primary device section
Found fglrx secondary device section
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-1

```

The last command you told me to try prints this.

```
Warning: Option 'UseFastTLS' doesn't affect running session.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-2

```

---

### Post by Vakman on 2011-09-04
Okay, interesting, we are already using that file anyway it seems.
Perhaps, we should install the drivers manually if you have the time.
Please visit this site and download the file here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Remove the current installation of drivers from Hardware Drivers and restart. You will not have graphic drivers install during this time.

Ensure that no others are installed before you restart by running:
```
sudo apt-get remove --purge xserver-xorg-video-radeon
```
It is likely these will not exist here anyhow.

To install the drivers manually, once downloaded, you can follow this guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually"), ask me if you need anything.

Also, once those are installed, attempt this:
```
 sudo aticonfig --initial -f
```
```
sudo aticonfig --set-pcs-str="DDX,EnableRandR12,FALSE"
```

---

