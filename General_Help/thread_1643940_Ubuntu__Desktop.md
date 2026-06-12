---
title: "Ubuntu  Desktop"
date: 2010-12-12
forum: General Help
---

### Post by penguinplus on 2010-12-12
I can't start the desktop effects. Can someone help?

---

### Post by migs73 on 2010-12-12
Could you be more specific about what you have tried.
Also could you tell us your graphics card specs (if known) if you don't know please post the output of;

```
lspci
```

Thanks

---

### Post by migs73 on 2010-12-12
> **migs73 said:**
> Could you be more specific about what you have tried.
Also could you tell us your graphics card specs (if known) if you don't know please post the output of;

```
lspci
```

Thanks

Sorry I am being a bit presumptious there. When I say 'post the output of'

I mean;
 Open a terminal (Ctrl+Alt+T) type in the code above (lspci)

Then copy the stuff that appears on the screen and post it back here in 'code tags' (click on the # sign on the top of the reply box).

---

### Post by penguinplus on 2010-12-12
WHen I try to use wobbly windows in compiz it doesn't affect anything. I also can't detect the monitor or some thing for changing it's settings.

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

```

---

### Post by Krytarik on 2010-12-12
You have an onboard video chip:
```
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2) 
```
Have you downloaded and enabled the proprietary Nvidia-drivers?

Check via "System -> Administration -> Hardware Drivers", in case it's not follow the dialog, which should appear.

After that you have write a "xorg.conf"-file, it specifies among other things what video driver and what options the "X Server" (desktop) shall use.
To write one:
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration (it doesn't matter if the displayed monitor is not exactly yours)
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

Reboot and enable the effects via "System -> Preferences -> Appearance -> Visual Effects", hopefully it works then.;)

---

### Post by penguinplus on 2010-12-13
there is no x sever in the Nvidia x sever settings. It just says "nvidia-settings configuration"

---

### Post by penguinplus on 2010-12-13
When I try to enable "Extra" in appearence settings the screen just flashes a bit then says "Desktop effects could not be enabled". sometimes it seached for drives.

---

### Post by Krytarik on 2010-12-13
> **penguinplus said:**
> there is no x sever in the Nvidia x sever settings. It just says "nvidia-settings configuration"
Did you follow my step-by-step-guide?

---

### Post by penguinplus on 2010-12-30
It isn't detecting the display monitor. Here are some of the pictures of the problem.

I click "normal" in the effects settings.

It searches for drivers.

The screen flashes a little then says "could not enable Desktop effects"

---

### Post by Krytarik on 2010-12-31
Once again, did you install the proprietary driver via "System -> Administration -> Hardware Drivers"?!

---

### Post by penguinplus on 2011-01-02
Sorry I didn't get what you ment before but now I do. I just upgraded to ubuntu 10.10. I don't see some of the things you tell me to press. here is a picture of what I see.

---

### Post by Krytarik on 2011-01-03
> **Krytarik said:**
> Once again, did you install the proprietary driver via "System -> Administration -> Hardware Drivers"?!
In 10.10 it is called "Additional Drivers", check if the proprietary driver is installed and activated.

---

