---
title: "paprefs shows up; padevchooser doesn't / RANDR missing / VNC"
date: 2010-06-20
forum: General Help
---

### Post by GraysonPeddie on 2010-06-20
Ubuntu Server: xtightvncserver
Windows Vista: TightVNC Viewer

Ubuntu 10.04 is what I'm using.

Here's what I get:

```
grayson@ubuserver:~$ padevchooser
Xlib:  extension "RANDR" missing on display ":1.0"
^C
grayson@ubuserver:~$ paprefs
Xlib:  extension "RANDR" missing on display ":1.0"
grayson@ubuserver:~$
```

The reason why I did Ctrl+C (^C) is because padevchooser does not show up. It did install properly. paprefs displays just fine.

Anyway, here is my hardware specs:

```
grayson@ubuserver:~$ lspci
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
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 4
00] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address
Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
C+ (rev 10)
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video an
d Audio Decoder (rev 03)
grayson@ubuserver:~$
```

Note that I don't run an X-Window server in my Ubuntu Server machine. I use VLC if I have to make some configurations that require the use of X-Window Server, such as MythTV. If I am running Ubuntu Desktop 10.04 in my home theater PC, I enable X11 forwarding when I need to SSH into my server.

---

