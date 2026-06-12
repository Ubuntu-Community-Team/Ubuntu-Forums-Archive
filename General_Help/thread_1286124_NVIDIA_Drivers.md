---
title: "NVIDIA Drivers"
date: 2009-10-08
forum: General Help
---

### Post by bruce leroy on 2009-10-08
After installing UBUNTU 9.04 from UBUNTU Studio (as suggested from other post due to slowed system), my system is still running slow.  Opening and closing windows and apps are delayed.  Sound is choppy.  How do I know that everything is installed properly and working?  How do I know if I have the right drivers for NVIDIA and running properly.

AMD Athlon 64, 2.2 Ghz, 1.5 gig ram, NVIDIA Geforce 6100 GPU.

---

### Post by karlson on 2009-10-08
> **bruce leroy said:**
> After installing UBUNTU 9.04 from UBUNTU Studio (as suggested from other post due to slowed system), my system is still running slow.  Opening and closing windows and apps are delayed.  Sound is choppy.  How do I know that everything is installed properly and working?  How do I know if I have the right drivers for NVIDIA and running properly.

AMD Athlon 64, 2.2 Ghz, 1.5 gig ram, NVIDIA Geforce 6100 GPU.


One thing to try would be to use a different driver for Nvidia and see if it does better.

You can also strace X to see if it is slowing down in any of the calls.

mpstat, iostat, top would be helpful too before you start going into the low level drivers.

---

### Post by OpenGuard on 2009-10-08
```
lspci | grep -i nvidia
```

What's the output ?

---

### Post by bruce leroy on 2009-10-09
Here's the output:
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
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)

---

