---
title: "Machine freezing"
date: 2010-04-13
forum: General Help
---

### Post by Scruff343 on 2010-04-13
Hi I just put Ubuntu on my partners machine as they were Windows 7 and it kept blue screening on them so automatically Ububntu went on.

But now it freezes and sometimes the Caps Lock and Scroll Lock keys flash when it freezes.  The machine is basically used for World of Warcraft so today I sat on it doing other more taxing things and it didn't freeze.  Could this be a hardware problem or compatibility issue as I honestly don't know what to do is there any programs that can check the hardware of even give me a more detailed report of why it is doing this.

Please reply ASAP
Thanks :D

---

### Post by sandyd on 2010-04-13
> **Scruff343 said:**
> Hi I just put Ubuntu on my partners machine as they were Windows 7 and it kept blue screening on them so automatically Ububntu went on.

But now it freezes and sometimes the Caps Lock and Scroll Lock keys flash when it freezes.  The machine is basically used for World of Warcraft so today I sat on it doing other more taxing things and it didn't freeze.  Could this be a hardware problem or compatibility issue as I honestly don't know what to do is there any programs that can check the hardware of even give me a more detailed report of why it is doing this.

Please reply ASAP
Thanks :D
the Caps Lock & the Scroll Lock light flashing are an indication of a kernel panic.
can you post the output of ```
lspci
```

---

### Post by Scruff343 on 2010-04-13
Hi the output is;

00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 SATA controller: nVidia Corporation GeForce 7100/nForce 630i SATA (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7050 / nForce 610i] (rev a2)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

Hope this can help you help me lol

---

