---
title: "Can't figure out how to set up wireless networking?"
date: 2012-01-28
forum: General Help
---

### Post by ray136 on 2012-01-28
Whenever I use the command(sudo lshw -C network), it gives me and output that is PCI (sysfs), instead of telling me my network adapter information. I honestly have no idea what's going on with this.

I have a Compaq Presario SR5152NX, running Ubuntu 11.04

---

### Post by bkratz on 2012-01-28
> **ray136 said:**
> Whenever I use the command(sudo lshw -C network), it gives me and output that is PCI (sysfs), instead of telling me my network adapter information. I honestly have no idea what's going on with this.

I have a Compaq Presario SR5152NX, running Ubuntu 11.04


You probably just didn't wait long enough to populate. You might try, which will give you all network device (with net in name)

```
lspci -nnk | grep -iA2 net
```

---

### Post by ray136 on 2012-01-28
> **bkratz said:**
> You probably just didn't wait long enough to populate. You might try, which will give you all network device (with net in name)

```
lspci -nnk | grep -iA2 net
```

That gave me this
```

00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:2a5b]
	Kernel driver in use: forcedeth

```
But I think that's my wired connection. I could be wrong though, I usually am when it comes to computer things.

---

### Post by bkratz on 2012-01-28
Try looking in lspci or lsusb.   Those are LSPCI and LSUSB (lowercase--just in case it uses an internal usb connection)

---

### Post by ray136 on 2012-01-28
> **bkratz said:**
> Try looking in lspci or lsusb.   Those are LSPCI and LSUSB (lowercase--just in case it uses an internal usb connection)

I'm assuming these go into the terminal right? I tried them and got this.
lspci
```


00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

```
and lsusb
```


Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 002: ID 1043:8012 iCreate Technologies Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

