---
title: "No Sound!"
date: 2010-04-01
forum: General Help
---

### Post by Sugoi48 on 2010-04-01
I have no sound anywhere! I've got the main volume up and alsamixer up and my speakers and headphone jack work on Mac OS. Any ideas? I'm on a MacBook Pro (june 2009 model, 15.4") and I'm running 9.10. Thank you!

---

### Post by koolblue3 on 2010-04-01
Hi,

Try right clicking the speaker in the top right corner of your screen and then clicking sound preferences, then in the window that pops up click the output tab. If there is more then one device under the "Choose a device for sound output" box click the radio button a next to the other device.

---

### Post by Sugoi48 on 2010-04-01
Under "Output" I only had "Internal Audio Analog Stereo". I also tried the four hardware profiles (Duplex, input, output, off) with no success. When I was checking the mic, it read one bar when fully amplified. Any other ideas? Thank you!

---

### Post by koolblue3 on 2010-04-01
Hi,

Could you please run the command ```
lspci
``` in a terminal and post the output of that command.

---

### Post by Sugoi48 on 2010-04-01
That gave me:

nigel@nigel-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)
nigel@nigel-laptop:~$

---

### Post by koolblue3 on 2010-04-01
Hi,

Thank you for posting the output of lspci it has helped me find a bug report similar to your problem. Check out this link I think it maybe able to help you with your issue [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483332](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483332).

---

