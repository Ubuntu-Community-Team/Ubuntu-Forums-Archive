---
title: "Monitor unknown &gt; How to force different screen resolution at startup?"
date: 2011-05-11
forum: General Help
---

### Post by lfys on 2011-05-11
Hi.

I recently started using Ubuntu 11.04.
Everything works fine with my monitor directly connected to the computer. I get a default screen resoluton of 1680 x 1050, which is just fine.

However, when I connect the screen through a **video splitter** to be able to use a beamer, the **screen resolution defaults to 1024x768**. Moreover, Ubuntu then detects an **unknown monitor** and I cannot select a higher resolution.

I searched for modifications of xrandr en xorg.conf but I have to admit I don't understand what I've read. So my question remains: **how can I force Ubuntu 11.04 to start with a screen resololution of 1680 x 1050** (without first connecting monitor only, that is).

Can someone give me an explanation-for-dummies to solve my problem?

I hereby add some information I retrieved with the screen connected without the splitter, so you can see what hardware is involved.

```
dirk@LaboFysica:~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0 
   1440x900       59.9 
   1024x768       75.1     60.0 
   800x600        75.0     60.3 
   640x480        75.0     60.0 
   720x400        70.1 
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

```
dirk@LaboFysica:~$ lspci
/knip/
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
/knip/
```

And in ect/gnome-settings-daemon/xrandr/monitors.xml I find

```

<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="VGA1">
          <vendor>MED</vendor>
          <product>0x86f6</product>
          <serial>0x01010101</serial>
          <width>1680</width>
          <height>1050</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI1">
      </output>
      <output name="DP1">
      </output>
  </configuration>
</monitors>
```

---

### Post by Grenage on 2011-05-11
The splitter will be blocking EDID signals, which tell the PC what kind out signal is optimal.  An xorg.conf is easy to setup if xrandr isn't working for you.

Rough guide [here]("http://www.grenage.com/xorg.html") (mine).  If you get stuck or feel lost, just post your monitor model and make, and I'll knock one up for you.  If someone else jumps in with some xrandr wizardry that works, so much the better!

---

### Post by lfys on 2011-05-12
Thank you for your kind help.
Since the computer is in a heavily used classroom, I will have to wait until next week to try things out.
In the mean while I will provide you with the specs I have found in the manual of the screen.

[INDENT]Trade Name: Medion
Type or Model Number: MD 30422 PV

Supported Display Settings
Resolution Horizontal Frequency Vertical Frequency
720 x 400 31.47 KHz 70 Hz
640 x 480 31.47 KHz 60 Hz
640 x 480 37.86 KHz 72.8 Hz
640 x 480 37.5 KHz 75 Hz
800 x 600 37.88 KHz 60.3 Hz
800 x 600 48.08 KHz 72.2 Hz
800 x 600 46.87 KHz 75 Hz
1024 x 768 48.36 KHz 60 Hz
1024 x 768 56.48 KHz 70.1 Hz
1024 x 768 60.02 KHz 75 Hz
1280 x 1024 80.00 KHz 75 Hz
1440 x 900 55.47 KHz 59.90 Hz
1680 x 1050* 64.67 KHz 60 Hz (*recommended physical resolution)[/INDENT]

Of course I would be very grateful with a ready-to-use solution.

---

### Post by Grenage on 2011-05-12
No problem, I'll knock one up at lunch time.

---

### Post by Grenage on 2011-05-12
Give this a whirl.  I couldn't find a manual for that monitor anywhere (there's usually a simple x-x, x-x for the ranges), so the frequencies are guesswork based on what you posted; the modeline *should* force your desired resolution.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Medion"
	ModelName "30422"
	HorizSync 30 - 80
	VertRefresh 60 - 75
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 4 Series"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
	EndSubSection
EndSection
```

---

### Post by leebrent on 2011-05-12
> **Grenage said:**
> The splitter will be blocking EDID signals, which tell the PC what kind out signal is optimal.  An xorg.conf is easy to setup if xrandr isn't working for you.

Rough guide [here]("http://www.grenage.com/xorg.html") (mine).  If you get stuck or feel lost, just post your monitor model and make, and I'll knock one up for you.  If someone else jumps in with some xrandr wizardry that works, so much the better!


Can you tell me if this video card is supported? I tried a couple drivers and it went sideways. The screens were frozen but showing Unity... I had to go back to classic to get to this forum. 

grenage@ublt:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

leeb@305-511-03b:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: G72 Board - p381n5 Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edid: 1 3
id: ad49
eisa: ACRad49
serial: 70106086
manufacture: 1 2007
input: sync on green, analog signal.
screensize: 38 30
gamma: 2.070000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@75
ctiming: 1280x1024@60
ctiming: 1152x864@75
ctiming: 1152x864@60
ctiming: 1024x768@75
ctiming: 1024x768@60
ctiming: 800x600@75
ctiming: 800x600@60
dtiming: 1280x1024@70
monitorid: L49081224201
monitorrange: 30-83, 55-75
monitorname: Acer AL1916
leeb@305-511-03b:~$

---

### Post by Grenage on 2011-05-12
> **leebrent said:**
> Can you tell me if this video card is supported? I tried a couple drivers and it went sideways. The screens were frozen but showing Unity... I had to go back to classic to get to this forum. 


Assuming you have a GeForce 7300 GS (your terminal output has one of my PC names and user name - from a guide?), it looks like others might be having the same problem:

[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/38728#38728](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity/38728#38728)

The good news is that it's probably temporary.

---

### Post by leebrent on 2011-05-12
Thank you, You are correct, I have a GeForce 7300GS with two monitors.

---

### Post by lfys on 2011-05-17
> **Grenage said:**
> Give this a whirl.  I couldn't find a manual for that monitor anywhere (there's usually a simple x-x, x-x for the ranges), so the frequencies are guesswork based on what you posted; the modeline *should* force your desired resolution.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Medion"
	ModelName "30422"
	HorizSync 30 - 80
	VertRefresh 60 - 75
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 4 Series"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
	EndSubSection
EndSection
```


This provides a (for me) satisfactory solution.

I made the etc/X11/xorg.conf with the code above.
Then I logged out and back in.
The derired resolution now does show up in the list.
Then I switched to this resolution. It does funny things with the screen but I accepted to keep it anyway.
Then I completely restarted the system.
Starting up leaves me with a low resolution.
However, after logging in, my desktop is OK at 1680x1050.
I consider the problem solved.
Thanks.

---

### Post by Grenage on 2011-05-17
Odd that the login screen uses a low res, but I'm glad that you have a workable solution.

---

