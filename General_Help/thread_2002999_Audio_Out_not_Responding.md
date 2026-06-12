---
title: "Audio Out not Responding"
date: 2012-06-13
forum: General Help
---

### Post by Rotblatt on 2012-06-13
Hey All,
I've been trying all the fixes for the frequently noted problems with audio outputs in Ubuntu.  I've used Alsamixer in terminal and tried the hda model = mb5 in the .conf file fix; however, none of these changes helped the current situations.

I'm currently running 11.10 on a macbook 5,2.
When I unmute the speakers, a red light appears inside only the audio out jack; however, no sound comes out of them regardless of the output I connect and the internal speakers are not never muted.
System Settings > Sound does not register any device, but Alsamixer does register my sound card as HDA NVIDA.
 
How can I get the system to register my audio out jack and mute the internal speakers when something is attached.

---

### Post by Kira_Belka on 2012-06-14
> **Rotblatt said:**
> Hey All,
I've been trying all the fixes for the frequently noted problems with audio outputs in Ubuntu.  I've used Alsamixer in terminal and tried the hda model = mb5 in the .conf file fix; however, none of these changes helped the current situations.

I'm currently running 11.10 on a macbook 5,2.
When I unmute the speakers, a red light appears inside only the audio out jack; however, no sound comes out of them regardless of the output I connect and the internal speakers are not never muted.
System Settings > Sound does not register any device, but Alsamixer does register my sound card as HDA NVIDA.
 
How can I get the system to register my audio out jack and mute the internal speakers when something is attached.

First of all please post result of executing "lspci".
and "ls /proc/asound".

---

### Post by Rotblatt on 2012-06-14
MacBook:~$ lspci
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
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
04:00.0 FireWire (IEEE 1394): Agere Systems Device 5903 (rev 07)

MacBook:~$ ls /proc/asound
card0  devices  modules  pcm  timers
cards  hwdep    NVidia   seq  version

---

### Post by Kira_Belka on 2012-06-14
I hope it helps:
[http://www.dbarticles.com/ubuntu-10-04-sound-issues-trying-to-find-the-right-sound-model/](http://www.dbarticles.com/ubuntu-10-04-sound-issues-trying-to-find-the-right-sound-model/)

what's version of your alsa drivers? you can see it in synaptic for example or in aptitude.

---

### Post by Rotblatt on 2012-06-14
My version is 1.0.24

I already changed the options hda=mb5

I also tried =macbook
neither one works.

---

