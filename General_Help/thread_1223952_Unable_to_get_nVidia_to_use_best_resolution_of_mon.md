---
title: "Unable to get nVidia to use best resolution of monitor (SyncMaster 2220WM)"
date: 2009-07-26
forum: General Help
---

### Post by indrajal on 2009-07-26
I had a power outage and after booting up again, I found that I'd lost my screen resolution. Try as I might, couldn't get the nVidia card to get the best resolution of the monitor (SyncMaster 2220WM) - 1680x1050.

ddcprobe gives:
```
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: Build    061010.3
product: MCP61 - mcp61-85 Chip Rev
memory: 65536kb
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
edidfail

```

lshw -C video gives:
```
*-display               
       description: VGA compatible controller
       product: GeForce 6150SE nForce 430
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

xorg.conf has this:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

Every time I've tried inserting a Mode in the Screen section, like below, the system pretty much refuses to accept the config file and I have to get that line out.
```
Mode "1680x1050@60"
```

Would appreciate some guidance on how to get back the best resolution of my LCD monitor. Thank you so much.

---

### Post by HappyFeet on 2009-07-26
Try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```and reboot.
Or
```
sudo dpkg-reconfigure xserver-xorg
```
and configure yourself, and reboot.

---

### Post by indrajal on 2009-07-27
I tried that several times before posting earlier. However, I've managed to resolve this issue-  it was a bizarre problem. It turns out I had too many wires near the monitor and there used to be a crackling sound that should have warned me about this. I rearranged my workspace, and reduced the wires near the monitor, and the crackling disappeared, and Ubuntu also picked up the right resolution.

---

