---
title: "Fixed my Nvidia nvrm error issue !!!"
date: 2010-09-28
forum: General Help
---

### Post by homerhomer on 2010-09-28
I noticed that my "trusty" Nvidia card was starting to act funny. I would get flashes reboots and just strange unstableness. 

I couldn't play anything in wine or opengl games. Yikes! 

Some of the errors I was getting in dmesg

NVRM: Xid (0002:00): 13, 0001 00000000 00005097 00000280 0003029e 0000000c
NVRM: Xid (0002:00): 13, 0001 00000000 00005097 000002c0 469e7c00 0000000c
NVRM: Xid (0002:00): 1, Channel 00000001 Method 00000000 Data 0303be00

I was certain it was "game over" for my video card. So I called and tried to RMA the thing. They made me go to a friends house to verify it on Windows ( yuk! ). Anyway, it didn't break while on Windows, huh?

Turns out it was the Nvidia driver Powermizer was stuff was killing everything. 

So I turned it off and life is good now.


To turn it off: (at least in 10.04 lucid)
Go to command line and open xorg.conf  ( sudo gedit /etc/X11/xorg.conf )
and add this line. You may have to create the file if it doesn't exist. 


Section "Device"
    Identifier      "Device0"
	Driver      "nvidia"
    	Option      "Coolbits" "1"
	Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x3"
	Option	    "AddARGBGLXVisuals" "true"
	Option 	    "ConnectToAcpid" "false"
        Option      "NoLogo" "true"
EndSection

---

