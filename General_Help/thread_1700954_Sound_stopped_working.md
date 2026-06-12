---
title: "Sound stopped working"
date: 2011-03-05
forum: General Help
---

### Post by cindyrella on 2011-03-05
Hi ubuntu community,

Three days ago, my sound stopped working. I didn't install any updates or download any new software. I'm using Hardy.

I have checked volume control -- nothing is muted. 

I am using a headset. (This shouldn't matter since the sound doesn't seem to work when I plug in my speakers.)

I did a hardware check and my sound card works perfectly fine. I hear the usual login sounds when Ubuntu starts. The device selected is currently "Capture: ALSA PCM on front:0 (ALC883 Analog) via DMA (Pulse Audio Mixer)." I have tried the other devices and the same problem persists.

I have already tried many of the suggestions on [this comprehensive thread]("http://ubuntuforums.org/showthread.php?t=205449"), but nothing has worked.

When I run:

```
sudo update-pciids; lspci
```

I get:

```

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
02:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)

```


When I run:

```
cat /proc/asound/card0/codec#* | grep Codec
```

I get:

```
Codec: Realtek ALC888
```


When I run:

```
aplay -l
```

I get:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Please let me know what I should do next.

UPDATE: I noticed one other thing. After I reboot, I try to play music on my computer and it works just fine. When I fire up Chrome, I try to chat or play a video and no sound comes out. I go back to playing music on my computer and that doesn't work either.

---

### Post by cindyrella on 2011-03-06
Bump.

---

