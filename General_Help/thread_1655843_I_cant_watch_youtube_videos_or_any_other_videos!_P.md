---
title: "I cant watch youtube videos or any other videos! Please help!"
date: 2010-12-30
forum: General Help
---

### Post by nosodaforme on 2010-12-30
HELLO!

im new to the whole ubuntu and linux experience and i had randomly downloaded it one day and have been using it ever since but to my dismay..my youtube videos or any other kind of video i try to watch online is green scrunched up and blurry i know the video is playing but i cant watch it.. i have no idea how to fix it! but if someone out there could help me to get this fixed you would have helped alot!!! 

THANKS!! =DDD

---

### Post by fibrebiz on 2010-12-30
Do you have the latest version of flash installed?

---

### Post by Verbeck on 2010-12-30
> [s]
install the package * ubuntu-restricted-extras* from the software center (in the applications menu) to get flash, java,  and audio/video codecs
more info here > [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

or if you want ONLY flash> install the* adobe flash plugin* [/s]


edit: oops. didn't read the entire post

---

### Post by ajgreeny on 2010-12-30
Can you also tell us a lot more about your hardware, in particular your graphics card.

If you are not sure, open a terminal from Applications ->Accessories, type, or copy/paste this command ```
lspci
``` and copy the output back here.

---

### Post by Paul41 on 2010-12-30
I see why Verbeck edited his response, but it is still a good question to ask just to be sure.  Did you install the ubuntu-restricted-extras?

---

### Post by nosodaforme on 2010-12-30
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

this is all it says about my hardware... but i dont think i have done restricted extras??

---

### Post by Paul41 on 2010-12-30
Try to install it to see if it makes a difference. 

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by karthick87 on 2010-12-30
Also install,

```
sudo apt-get install  flashplugin-nonfree 
```

---

### Post by Paul41 on 2010-12-30
> **karthick87 said:**
> Also install,

```
sudo apt-get install  flashplugin-nonfree 
```

This package is included with the restricted extras.

---

### Post by ajgreeny on 2010-12-30
You may also need to make sure you have the right driver for your graphics card installed and working, so go to **System ->Administration ->Additional Drivers** to see fi any options appear.

Also check to see if **gnash** is installed and if it is, remove it.

---

### Post by karthick87 on 2010-12-30
Oke thanks for the information :)

---

### Post by nosodaforme on 2010-12-30
ok so i installed the packages and the videos are still messed up ans some still say adobe flash player has crashed how do i un install gnash sorry noob here =p

---

### Post by nosodaforme on 2010-12-30
so how do i uninstall gnash? also i had two drivers one was version 173 and the other was the one i was using. im so confused =[

---

### Post by gordintoronto on 2010-12-30
Run System/Administration/Synaptic Package Manager, search (not quick search) for gnash, right-click it, "mark for removal," then click "Apply."

---

### Post by karthick87 on 2010-12-30
```
sudo apt-get remove gnash
```

---

