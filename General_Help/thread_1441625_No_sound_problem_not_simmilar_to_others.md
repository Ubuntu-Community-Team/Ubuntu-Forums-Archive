---
title: "No sound problem not simmilar to others"
date: 2010-03-29
forum: General Help
---

### Post by tetsuo2010 on 2010-03-29
i've been having an ongoing problem since i've used Ubuntu. specifically my sound does not like to work when i unplug the speakers and then plug them back in. i know my speakers are fine, in fact i had sound today. when i needed sound for my laptop however, i unplugged them from my desktop. after plugging them back in i had no sound. 

also, my speaker icon dissapeared...it's not near my inernet connectivity icon like it usually is. i know for a fact ALSA is installed and worked fine. pulseaudio is installed and works. i know very little about Ubuntu. i unfortunatley can't remember what fixes this problem, but there has to be something that's keepin ubuntu from recognizing my speakers, or outputing the sound. any help would be great!

i am using Ubuntu 9.04 64 bit
and my sound card works just fine but if u need any spec i'd be glad to give

---

### Post by roh8880 on 2010-07-01
Same issue with 10.04

I rebooted my compy and nothing. I went to [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but when I got to the chipset part of the diagnosis, I followed the link and there was nothing there but a [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

It started out as me having to open the sound preferences before my sound would stay on. Sound would work normally at start up for a few seconds. Then cut out till I opened the sound preferences and left it open. Now nothing. My system recognises my sound card > **** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: SB [HDA ATI SB], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and 
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 82ee
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=8]
	I/O ports at 8000 [size=4]
	I/O ports at 7000 [size=16]
	Memory at f7fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f7fff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f7ffa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 82ea
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000e000-0000efff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ff9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
	Subsystem: eVga.com. Corp. Device c958
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fbe80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 82c6
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at d800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f6ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at e800 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

This is really frustrating. Can anyone help out with this?

---

### Post by roh8880 on 2010-07-05
Bump if anyone cares

Here is my also info . . .

[http://www.alsa-project.org/db/?f=4ffe2ce194d68413d5604d4e86bafa6e6c3b70dc](http://www.alsa-project.org/db/?f=4ffe2ce194d68413d5604d4e86bafa6e6c3b70dc)

---

### Post by roh8880 on 2010-07-05
Fixed by the following instructions from [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


> Reinstalling ALSA
It is also possible something has gone really wrong with the ALSA drivers or there is a problem with some configuration file that got messed up with all that fooling around from above. You can try purging and reinstalling ALSA. (I recently had to do this after replacing my motherboard, the new on-board sound card was correctly detected but my existing pci sound card was not, weird...)


(1) Remove the ALSA packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
Code:

sudo apt-get install gdm ubuntu-desktop

Reboot

I had to do this twice to get it fixed. This is only a quick fix. There is a bug in the 10.04 distro of Ubuntu with the Alsa program. As of right now there is no permanent fix, so this process may have to be repeated whenever the problem arises again.

Also, there may be some things missing on the desktop or the menu icons. They are still there, just not visible. Just click on the place where it should be, repeat the process above, and reboot. This should clear that up. Still waiting on a final fix for this problem. It gets annoying.

---

### Post by thorapikc8 on 2011-01-07
> **roh8880 said:**
> Same issue with 10.04I rebooted my compy and nothing. I went to [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but when I got to the chipset part of the diagnosis, I followed the link and there was nothing there but a [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)It started out as me having to open the sound preferences before my sound would stay on. Sound would work normally at start up for a few seconds. Then cut out till I opened the sound preferences and left it open. Now nothing. My system recognises my sound card 	Quote:				 							**** List of PLAYBACK Hardware Devices ****card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]  Subdevices: 1/1  Subdevice #0: subdevice #0card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]  Subdevices: 1/1  Subdevice #0: subdevice #0card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]  Subdevices: 1/1  Subdevice #0: subdevice #0card 1: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]  Subdevices: 1/1  Subdevice #0: subdevice #0card 2: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]  Subdevices: 2/2  Subdevice #0: subdevice #0  Subdevice #1: subdevice #1card 2: SB [HDA ATI SB], device 1: VT1708B Digital [VT1708B Digital]  Subdevices: 1/1  Subdevice #0: subdevice #0					 	 	and 	Quote:				 							00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge	Subsystem: ASUSTeK Computer Inc. Device 82ee	Flags: bus master, 66MHz, medium devsel, latency 0	Capabilities: 00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)	Flags: bus master, fast devsel, latency 0	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0	I/O behind bridge: 0000c000-0000cfff	Memory behind bridge: f8000000-fbefffff	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff	Capabilities: 	Kernel driver in use: pcieport	Kernel modules: shpchp00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)	Flags: bus master, fast devsel, latency 0	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0	I/O behind bridge: 0000d000-0000dfff	Memory behind bridge: fbf00000-fbffffff	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff	Capabilities: 	Kernel driver in use: pcieport	Kernel modules: shpchp00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22	I/O ports at b000 [size=8]	I/O ports at a000 [size=4]	I/O ports at 9000 [size=8]	I/O ports at 8000 [size=4]	I/O ports at 7000 [size=16]	Memory at f7fff800 (32-bit, non-prefetchable) [size=1K]	Capabilities: 	Kernel driver in use: ahci	Kernel modules: ahci00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16	Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]	Kernel driver in use: ohci_hcd00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16	Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]	Kernel driver in use: ohci_hcd00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17	Memory at f7fff000 (32-bit, non-prefetchable) [size=256]	Capabilities: 	Kernel driver in use: ehci_hcd00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)	Subsystem: ASUSTeK Computer Inc. [[COLOR=#000000]Device[/COLOR]](http://www.convertvideofiles.net/convert-mod-files/convert-mod-files-to-iaudio.html) 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18	Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]	Kernel driver in use: ohci_hcd00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18	Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]	Kernel driver in use: ohci_hcd00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19	Memory at f7ffa800 (32-bit, non-prefetchable) [size=256]	Capabilities: 	Kernel driver in use: ehci_hcd00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: 66MHz, medium devsel	Capabilities: 	Kernel modules: i2c-piix400:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16	I/O ports at 01f0 [size=8]	I/O ports at 03f4 [size=1]	I/O ports at 0170 [size=8]	I/O ports at 0374 [size=1]	I/O ports at ff00 [size=16]	Capabilities: 	Kernel driver in use: pata_atiixp	Kernel modules: pata_atiixp00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)	Subsystem: ASUSTeK Computer Inc. Device 82ea	Flags: bus master, slow devsel, latency 64, IRQ 16	Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]	Capabilities: 	Kernel driver in use: HDA Intel	Kernel modules: snd-hda-intel00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 000:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)	Flags: bus master, 66MHz, medium devsel, latency 64	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64	I/O behind bridge: 0000e000-0000efff00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)	Subsystem: ASUSTeK Computer Inc. Device 82ef	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18	Memory at f7ff9000 (32-bit, non-prefetchable) [size=4K]	Kernel driver in use: ohci_hcd00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration	Flags: fast devsel	Capabilities: 00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map	Flags: fast devsel00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller	Flags: fast devsel00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control	Flags: fast devsel	Capabilities: 00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control	Flags: fast devsel01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)	Subsystem: eVga.com. Corp. Device c958	Flags: bus master, fast devsel, latency 0, IRQ 18	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]	Memory at d0000000 (64-bit, prefetchable) [size=256M]	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]	I/O ports at cc00 [size=128]	[virtual] Expansion ROM at fbe80000 [disabled] [size=512K]	Capabilities: 	Kernel driver in use: nvidia	Kernel modules: nvidia-current, nvidiafb, nouveau02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)	Subsystem: ASUSTeK Computer Inc. Device 82c6	Flags: bus master, fast devsel, latency 0, IRQ 27	I/O ports at d800 [size=256]	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]	Memory at f6ff0000 (64-bit, prefetchable) [size=64K]	Expansion ROM at fbfc0000 [disabled] [size=128K]	Capabilities: 	Kernel driver in use: r8169	Kernel modules: r816903:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)	Subsystem: C-Media Electronics Inc CM8738	Flags: bus master, medium devsel, latency 64, IRQ 20	I/O ports at e800 [size=256]	Capabilities: 	Kernel driver in use: C-Media PCI	Kernel modules: snd-cmipci					 	 	This is really frustrating. Can anyone help out with this?What's the problem? The link cannot be opened.

---

