---
title: "Please help with nvidia driver EDID problem---my install is unusable!"
date: 2010-11-22
forum: General Help
---

### Post by rende on 2010-11-22
I have been using Ubuntu 10.04 x86 64-bit for several months now.  It was working fine.  A few weeks ago, I restarted and my monitor refused to go above 640x480 resolution.  It is next to impossible for me to use for my work in this resolution.

I have an NVIDIA GeForce 9800 GTX+ and an Acer AL2216W LCD monitor.  I do not know if the problem occurred after upgrading the nvidia driver or what exactly happened, but I tracked the issue down to an invalid EDID checksum:
```

(WW) Nov 22 21:33:35 NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) Nov 22 21:33:35 NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
(--) Nov 22 21:33:35 NVIDIA(GPU-0):
(--) Nov 22 21:33:35 NVIDIA(GPU-0): Raw EDID bytes:
(--) Nov 22 21:33:35 NVIDIA(GPU-0):
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  04 72 74 ad 74 13 20 64
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   2a 10 01 03 e8 2f 1e 78  2e c5 85 a4 59 49 9a 24
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   12 50 54 bf ef 00 81 80  81 40 71 4f 95 00 95 0f
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   b3 00 81 c0 8b c0 21 39  90 30 62 1a 27 40 68 b0
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   36 00 d9 28 11 00 00 1c  00 00 00 fd 00 38 4c 1e
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   52 15 00 0a 20 20 20 20  20 20 00 00 00 fc 00 41
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   63 65 72 20 41 4c 32 32  31 36 57 0a 00 00 00 b0
(--) Nov 22 21:33:35 NVIDIA(GPU-0):   00 45 54 4c 37 34 30 39  30 33 38 20 20 20 00 53

```

OK, So I found an EDID for my monitor that supposedly works (i.e. it is said to have the correct checksum).  I put this into a file and convert it to binary and use hexedit to make sure it is correct.  The hexdump is:

```

rende@mycomp:~$ xxd edid.bin
0000000: ffff ffff ffff 0004 7274 ad96 0420 7216  ........rt... r.
0000010: 0000 5054 bfef 0081 8081 4071 4f95 0095  ..PT......@qO...
0000020: 0fb3 0000 0000 0000 0000 0000 0000 0000  ................
0000030: 0000 0000 0000 00d9 2811 0000 1c00 0000  ........(.......
0000040: fd00 384c 1e52 0000 0000 0000 0000 0000  ..8L.R..........
0000050: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000060: 0000 0065 7220 414c 3232 3136 570a 0000  ...er AL2216W...
0000070: 00ff 00

```            

OK so just the last line changed.  Now, I generate X11.conf using nvidia-xconfig --custom-edid=edid.bin and use this new X11.conf.  But, I get the following error now in my X11.log:

```


(WW) Nov 22 21:33:35 NVIDIA(0): No display device specified for CustomEDID "/tmp/edid.bin";
(WW) Nov 22 21:33:35 NVIDIA(0):     ignoring.

```

It then goes on to use the same EDID with the invalid cheksum as it did before I tried to use the custom EDID.  I just can't get it to use the custom edid.

I am pretty much at my wit's end at this point.  I have been using Ubuntu for years but I simply can't productively use my computer in this resolution.  If I can't get this resolved I will have to try other distros but I would prefer to stick with Ubuntu, so if you have any ideas I can try please let me know!


Here are the relative portions of my X11.conf:

```


Section "Monitor"

       # Block type: 2:0 3:fd
       # Block type: 2:0 3:fc
       # Block type: 2:0 3:fd
    Identifier     "Acer AL2216W"
    VendorName     "ACR"
    ModelName      "Acer AL2216W"
    HorizSync       31.5 - 67.0
    VertRefresh     50.0 - 75.0
    ModeLine       "1680x1050" 149.00 1680 1760 1944 2280 1050 1050 1052 1
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option         "CustomEDID" "/tmp/edid.bin"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Acer AL2216W"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by rende on 2010-11-23
OK, I fixed it but still don't know why I couldn't get the Custom EDID to work.  

The xorg.conf that did the trick is at the end of this post.

I got the monitor section by doing:

sudo apt-get install read-edid
then
sudo get-edid | parse-edid

Then I added 
    Option         "UseEDID" "False"
    Option         "ExactModeTimingsDVI"      "True"
to the Screen section

and 

    Option	"ModeValidation" "NoEdidModes"

to the Device section.  Theoretically all options could go in the screen section but this is how I did it and it worked so I'm not touching the thing again ;) 


```

Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "Monitor0"
	VendorName "ACR"
	ModelName "Acer AL2216W"
	# Block type: 2:0 3:fd
	HorizSync 30-82
	VertRefresh 56-76
	# Max dot clock (video bandwidth) 210 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:b0
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1680x1050"	# vfreq 59.954Hz, hfreq 65.290kHz
		DotClock	146.250000
		HTimings	1680 1784 1960 2240
		VTimings	1050 1053 1059 1089
		Flags	"+HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:b0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option	"ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEDID" "False"
    Option         "ExactModeTimingsDVI"      "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x1440" "1360x850" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

---

### Post by deano_ferrari on 2010-11-27
No device was specified in your "CustomEDID" option. It needs the display device port reference eg CRT-0, DVI-0, or similar. You can get that info from your Xorg log, or via the 'xrandr' command. So for example (with a VGA connected montor):

```
Option "CustomEDID" "CRT-0:/full/path/to/edid.bin"
```

---

