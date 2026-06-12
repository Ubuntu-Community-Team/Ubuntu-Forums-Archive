---
title: "Cursor distorted (9.04)"
date: 2009-08-25
forum: General Help
---

### Post by Russell_S on 2009-08-25
Hi, I have a strange graphics problem that, hopefully, someone will be able to advise on.

I am running Ubuntu 9.04 which, up until today, has been displayed on a Samsung 17in LCD monitor with no issues. I have just bought a new iiyama 22in WS monitor and set it up as the main display with the old Samsung as a second monitor in a dual monitor setup. This worked fine and I have both monitors working side by side with each one at it's native resolution and all is well.

The problem that I am having is that at certain points across both displays the cursor gets corrupted. This only happens at six points across the width of the display and the area effected is only about 7mm wide but occurs all the way up the display at that point. The distance between the six places appears to be the same and continues across both monitors. Here are some photo's I have taken to show the kind of effect:

[IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Ubuntu%20Cursor%20Pics/IMG_0627.jpg[/IMG][IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Ubuntu%20Cursor%20Pics/IMG_0628.jpg[/IMG][IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Ubuntu%20Cursor%20Pics/IMG_0629.jpg[/IMG][IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Ubuntu%20Cursor%20Pics/IMG_0630.jpg[/IMG][IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Ubuntu%20Cursor%20Pics/IMG_0631.jpg[/IMG][IMG]http://i93.photobucket.com/albums/l74/RussellS_2006/Ubuntu%20Cursor%20Pics/IMG_0632.jpg[/IMG]


These pictures were taken without moving the cursor and the lines next to the cursor flicker. As soon as you move the cursor a few millimeters either way the corruption dissapears and the cursor is normal again. If I disable the second monitor and return to a single display setup again the problem disappears.

Here is the output of "lspci" to show my graphics card hardware etc:

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
02:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
```I am using the standard Ubuntu graphics driver (NOT the ATI one). The resolutions that the two monitors are set at are:

iiyama        1680x1050
Samsung    1280x1024


Obviously, this is not a major issue but is a bit annoying. If anyone has any ideas I would be gratefull.


Regards

Russell
[IMG]http://http://i93.photobucket.com/albums/l74/RussellS_2006/Ubuntu%20Cursor%20Pics/IMG_0629.jpg[/IMG]

---

