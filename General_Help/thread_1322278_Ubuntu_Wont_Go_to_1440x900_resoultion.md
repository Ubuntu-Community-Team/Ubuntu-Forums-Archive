---
title: "Ubuntu Wont Go to 1440x900 resoultion"
date: 2009-11-10
forum: General Help
---

### Post by Istonian on 2009-11-10
I recently installed Ubuntu 9.10 and I cannot get the 1440x900 resolution my monitor is supposed to be at. I have an Acer AL1916 W LCD 19" Screen. I have an nvidia 8600 gt graphics card. The highest option that is displayed is 1024x768. Here is my lspci output

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
I know you can generate the proper modelines with
```

cvt 1440 900

```

I do not, however, know how to properly insert those modelines into xorg.conf.

---

### Post by Istonian on 2009-11-10
> **ST3ALTHPSYCH0 said:**
> I know you can generate the proper modelines with
```

cvt 1440 900

```

I do not, however, know how to properly insert those modelines into xorg.conf.

I heard that ubuntu took the use of the xorg.conf file out. If there is anyway to put the mode line in and create an xorg.conf file I would appreciate your help on how to do that.

---

### Post by dbyjazz on 2009-11-10
you can still make changes to your xorg.conf file.

```
gksudo gedit /etc/X11/xorg.conf
```

then paste this

```
#Custom Xorg 

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
SubSection "Display"
        Depth 24
        Modes "1440x900"
        Virtual 1440 900
EndSubsection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by dbyjazz on 2009-11-10
.

---

### Post by Giblet5 on 2009-11-10
> **dbyjazz said:**
> you can still make changes to your xorg.conf file.

```
gksudo gedit /etc/X11/xorg.conf
```

then paste this


Try this one. 55.93Khz is the required horizontal sync frequency to paint 1440 pixels.

```
#Custom Xorg
# Tweaked by Giblet5 - if it works, name first-born "Giblet"

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
        Identifier      "Default Monitor"
        HorizSync       55.93 - 55.93
        VertRefresh     60.0 - 60.0
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device          "Default Device"
        Monitor         "Default Monitor"
	DefaultDepth	24
EndSection
```

Now, restart X via ```
sudo /etc/init.d/gdm restart
```

If it causes black screen, flip to console via Ctrl+Alt+F1, log in, and run ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo /etc/init.d/gdm restart
```

Write that down if you won't remember it.

---

### Post by Istonian on 2009-11-10
> **Giblet5 said:**
> Try this one. 55.93Khz is the required horizontal sync frequency to paint 1440 pixels.

```
#Custom Xorg
# Tweaked by Giblet5 - if it works, name first-born "Giblet"

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
        Identifier      "Default Monitor"
        HorizSync       55.93 - 55.93
        VertRefresh     60.0 - 60.0
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device          "Default Device"
        Monitor         "Default Monitor"
	DefaultDepth	24
EndSection
```

Now, restart X via ```
sudo /etc/init.d/gdm restart
```

If it causes black screen, flip to console via Ctrl+Alt+F1, log in, and run ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo /etc/init.d/gdm restart
```

Write that down if you won't remember it.

Thank you sooo much for your help. That worked! +1 for the helpful community.

---

### Post by Istonian on 2009-11-10
I have just one more question. The monitor is supposed to run at 75 hz refresh rate. The 60 hz looks very very flickery. Any way to change this?

---

### Post by Giblet5 on 2009-11-10
Easy. And we're very slowly learning what the actual capabilities of your monitor are, one resolution at a time! ;)

Please don't forget to mark this SOLVED via the Thread Tools dropdown at the top of this page. This is a common problem and I'm REALLY tired of plugging in the same stuff! People can search on SOLVED.

Change xorg.conf again, then restart Xorg as before.

```
#Custom Xorg
# Tweaked (again) by Giblet5 - if it works, name second-born "Pockpe Quordblot"

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
        Identifier      "Default Monitor"
        HorizSync       55.93 - 70.64
        VertRefresh     60.0  - 75.0
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device          "Default Device"
        Monitor         "Default Monitor"
	DefaultDepth	24
EndSection
```


It sounds like I'm doing magic, huh?

All I did was find out the HorizSync value from the cvt command: ```
cvt 1440 900 60
# 1440x900 59.89 Hz (CVT 1.30MA) [COLOR="DarkRed"]**hsync: 55.93**[/COLOR] kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

That gave me 55.93 for HorizSync and 60.0 for VertRefresh.

Then you're not HAPPY with that, oh noez. No, you want 75hz VertRefresh... ;)

```
cvt 1440 900 75
# 1440x900 74.98 Hz (CVT 1.30MA) [COLOR="DarkRed"]**hsync: 70.64**[/COLOR] kHz; pclk: 136.75 MHz
Modeline "1440x900_75.00"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
```


It's like finding out there's no Santa Claus, huh?

---

### Post by rifak on 2009-11-10
if you don't want to have an xorg file, you can use xrandr. with you monitor plugged in, what is the output of:

```
gtf 1440 900 75
```

---

### Post by Giblet5 on 2009-11-10
> **ego-sum-deus said:**
> if you don't want to have an xorg file, you can use xrandr. with you monitor plugged in, what is the output of:

```
gtf 1440 900 75
```

He's got an nvidia card. He *has* to have an xorg.conf.

Nvidia cards are very good at reading DDCC and EDID from monitors ..... when the right cables are present. Xrandr can't do anything that the nvidia driver won't also do.

---

### Post by rifak on 2009-11-10
ah, ok...my bad

---

### Post by Istonian on 2009-11-11
For some reason I still only get 60 hz as an option after changing my file. I would let it go, but my monitor flickers unless its at 75.

---

### Post by kio_http on 2009-11-11
I would recommend installing nvidia X server settings. That way you can customize Graphic options with GUI.

Similar to NVIDIA Control Panel in Windows

---

### Post by Giblet5 on 2009-11-11
> **Istonian said:**
> For some reason I still only get 60 hz as an option after changing my file. I would let it go, but my monitor flickers unless its at 75.

OK...

Same routine:

```
#Custom Xorg
# Tweaked (yet again) by Giblet5 - if it works, name second-born "Rackne Cobblepot"

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
        Identifier      "Default Monitor"
        HorizSync       70.64 - 70.64
        VertRefresh     74.98 - 74.98
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device          "Default Device"
        Monitor         "Default Monitor"
	DefaultDepth	24
EndSection
```


(It would be far better if you got the real frequency ranges from your monitor's vendor and used those, but this should work)

---

### Post by Mariane on 2009-11-12
> **kio_http said:**
> I would recommend installing nvidia X server settings.


Which packet would that be, please? 

I tried:
apt-cache search nvidia | grep server

and I have many answers:
xserver-xorg-video-nv - X.Org X server -- NV display driver
linux-restricted-modules-2.6.24-16-server - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-18-server - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-19-server - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-21-server - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-22-server - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-23-server - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-25-server - Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-24-server - Non-free Linux 2.6.24 modules on x86/x86_64


Mariane

---

### Post by Arup on 2009-11-12
The default Ubuntu nvidia driver in the repo doesn't create a xorg.conf file for some reason, however just do a gksudo nvidia-xconfig in terminal and that should make a file for you, then do a gksudo nvidia-xconfig, set your resolution there and save it to x, you can also set your refresh rates there.

---

