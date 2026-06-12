---
title: "How to check and install the drivers for graphics card?"
date: 2012-01-05
forum: General Help
---

### Post by kanada3 on 2012-01-05
My laptop is Asus X53S. I have two graphics card. Nvidia and Intel integrated. How do I check what drivers need to install the Intel?

---

### Post by meetdilip on 2012-01-05
Settings > Hardware > Additional drivers

---

### Post by kanada3 on 2012-01-05
That is not what I mean. There only installs the drivers for nvidia, and I want to install the drivers from Intel.

---

### Post by xc3RnbFO8P on 2012-01-05
Maybe here:
[https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/~hybrid-graphics-linux")
[http://linux-hybrid-graphics.blogspot.com/]("http://linux-hybrid-graphics.blogspot.com/")

---

### Post by meetdilip on 2012-01-05
An easier way will be to go to Asus site and get drivers for Ubuntu. Not sure Asus offer such an option but if it does, things will be very easy.

---

### Post by Mark Phelps on 2012-01-05
If you're trying to install drivers for BOTH graphics devices because you want to use switchable graphics in Linux -- you can't do that.  You have to disable ONE of the graphics devices in order to use the other.

See the thread below:

[http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html]("http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html")

---

### Post by kanada3 on 2012-01-05
I can't cope. Intel graphics card is the default in Ubuntu. Maybe it install the drivers? Hard info shows i915 kernel.
I do not know what drivers to download because it is their lot.

Card is intel hd graphics 6000.

---

### Post by topsites on 2012-01-05
If it works, don't fix it.

---

### Post by imachavel on 2012-01-05
> **kanada3 said:**
> I can't cope. Intel graphics card is the default in Ubuntu. Maybe it install the drivers? Hard info shows i915 kernel.
I do not know what drivers to download because it is their lot.

Card is intel hd graphics 6000.

please restart computer and go to bios. find out from looking through settings please if graphic adapter being used is onboard or added in. nvidia I'm guessing is added in and you don't want to use it anymore. If you remove the graphics card from the pci or agp slot, onboard will automatically be selected. ok?

also use this:

[http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/](http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/)

lspci
 $ lspci -v
 $ lspci -v | less

please post results here. Now once we find out what exact hardware you are using, you can go to, well not intel. Intel will give you a stupid driver finder utility. But if you want to use add in gpu, you can go go nvidia web site, look for the driver for your model of graphics card. If not, find out mobo manufacturer, then go to mobo manufacturer web site and download driver for your card. then You may need to install restricted drivers.

If I were you though, I would first restart your pc, I'm not sure what model of mobo you have, so won't know f2 key needed to get into firmware or bios settings, probably f2, maybe del. Usually 9/10 it's f2. It would be easier to only have one gpu installed, if onboard intel chip set is what you want to use, then maybe remove gpu. Either way more info would be helpful, with me so far?;)

---

### Post by imachavel on 2012-01-05
> **topsites said:**
> If it works, don't fix it.

this is also true, what is your screen resolution? What is wrong that you want to switch? 

this is terminal version:

[http://www.perpetualpc.net/srtd_resolution.html](http://www.perpetualpc.net/srtd_resolution.html)

if it's painful, then try searching 'monitors', it should give you an option to change the screen resolution.

---

### Post by Mark Phelps on 2012-01-05
> **kanada3 said:**
> My laptop is Asus X53S. I have two graphics card. Nvidia and Intel integrated. How do I check what drivers need to install the Intel?

If you're running off the Intel chipset, then the graphics drivers have already been installed.  This is not Windows -- where the first thing you do is go rummaging around for new drivers; in Linux, the drivers are automatically found and installed for you as part of the initial setup.

But ... as I said, if you are using the Intel chipset now and want to use the Nvidia chipset instead, you will need to figure out how to disable the Intel chipset -- and if you're dual-booting with Windows, you will most probably have to do this in the BIOS, which will "break" switchable graphics support in Windows.

---

### Post by imachavel on 2012-01-05
oh my mistake, this is the 'optimus' configuration isn't it? Didn't see laptop. Yeah my bad I've heard some stuff about these optimus technology laptops. Never actually used one :(

---

### Post by kanada3 on 2012-01-06
I want to install the drivers because the fan are working loud on a laptop and the battery runs out max 2 hours instead of four as in win7. Currently I have a system without  xorg. When install the drivers for nvidia and generate xorg file after reboot the system will not start. So it seems that default is the Intel graphics. But I'm not sure.
After installing the nvidia card writes, "is installed and is in use." I do not know how to properly configure xorg.

In the BIOS I don't have that option off the graphics card.


```


lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dc000000-dd0fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 15f2
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at dd400000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at df60a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at df608000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device 1ac3
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at df600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: dec00000-df5fffff
	Prefetchable memory behind bridge: 00000000d3700000-00000000d40fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: de200000-debfffff
	Prefetchable memory behind bridge: 00000000d2c00000-00000000d35fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: dd800000-de1fffff
	Prefetchable memory behind bridge: 00000000d2100000-00000000d2afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at df607000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at e0b0 [size=8]
	I/O ports at e0a0 [size=4]
	I/O ports at e090 [size=8]
	I/O ports at e080 [size=4]
	I/O ports at e060 [size=32]
	Memory at df606000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: medium devsel, IRQ 11
	Memory at df605000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 15f2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at d000 [size=128]
	Expansion ROM at dd000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: AzureWave Device 2c37
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at de200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1277
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at a000 [size=256]
	Memory at d2104000 (64-bit, prefetchable) [size=4K]
	Memory at d2100000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```
```


 lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

---

### Post by Catharsis on 2012-01-06
What are you trying to do?

The drivers for your Intel integrated graphics are already installed by default when you installed Ubuntu. And you seem to have found out how to install the nVidia drivers through Additional Drivers.

You can't run them both at once; you can either use the Intel integrated graphics or the nVidia GPU. If you're curious which driver you're using, you can check /var/log/Xorg.0.log. Are you asking how to use one and not the other?

---

### Post by kanada3 on 2012-01-06
I want to use one graphics card, but I do not know which.

---

### Post by Mark Phelps on 2012-01-06
Read the following info on switchable graphics. Since this feature was designed to work with MS Windows, there is no easy way to get around it in Linux: 

[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/]("http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/")

---

### Post by kanada3 on 2012-01-07
I installed Ironhide and I worked it out
Thanks.

---

