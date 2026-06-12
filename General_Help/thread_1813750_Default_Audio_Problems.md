---
title: "Default Audio Problems"
date: 2011-07-28
forum: General Help
---

### Post by Esahp on 2011-07-28
For some reason on any application that uses sound, but doesn't allow me to specify the input/output audio devices I don't get anything. I want all audio to go to my USB Headset, and not the onboard soundcard.

If anyone could help me sort this issue out that would be fantastic.

**To start off with, here's alsamixer:**
[IMG]http://i.imgur.com/3PT9D.png[/IMG]

**Here's a screenshot from Mumble (voice chat) that shows that I've set the USB headset device in there, and it works 100% fine on Mumble.**
[http://i.imgur.com/bv7lO.png](http://i.imgur.com/bv7lO.png)


**$ aplay -l**
> 
**** List of PLAYBACK Hardware Devices ****
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


**$ lspci -v**
> 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 30100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 20e0 [size=8]
	Memory at 20000000 (32-bit, prefetchable) [size=256M]
	Memory at 30180000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 301c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 30200000-303fffff
	Prefetchable memory behind bridge: 0000000030400000-00000000305fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 30600000-307fffff
	Prefetchable memory behind bridge: 0000000030800000-00000000309fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 30a00000-30bfffff
	Prefetchable memory behind bridge: 0000000030c00000-0000000030dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: 30e00000-30ffffff
	Prefetchable memory behind bridge: 0000000031000000-00000000311fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: 31200000-313fffff
	Prefetchable memory behind bridge: 0000000031400000-00000000315fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 2020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 301c4400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 30000000-300fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: leds-ss4200, iTCO_wdt

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Gateway 2000 Device 6051
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 20a0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	Subsystem: Gateway 2000 Device 6051
	Flags: medium devsel, IRQ 11
	I/O ports at 2000 [size=32]
	Kernel modules: i2c-i801

06:01.0 Communication controller: Conexant Systems, Inc. Device 2f40
	Subsystem: Conexant Systems, Inc. Device 2000
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 9
	Memory at 30000000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at 1040 [size=8]
	Capabilities: <access denied>

06:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
	Subsystem: Gateway 2000 Device 0001
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at 30010000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100


**$ cat /etc/modprobe.d/alsa-base.conf**
> 

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
#options snd-usb-audio index=-2

#My Edits
options snd_usb_audio index=0
options snd_hda_intel index=1


As you can see from the alsa-base.conf above I've tried specifying snd_usb_audio as the default device, but it's not working.

Any help would be greatly appreciated.

Thanks

---

### Post by mikewhatever on 2011-07-28
Try using the Sound Preferences, Output tab. If the USB headset is detected, it should be there as a selectable device.

---

### Post by Esahp on 2011-07-28
> **mikewhatever said:**
> Try using the Sound Preferences, Output tab. If the USB headset is detected, it should be there as a selectable device.

lubuntu doesn't have that in the default menus, what would I need to install to get it?

---

### Post by mikewhatever on 2011-07-28
Apologies, I must have missed the Lubuntu part. What about the speaker icon in the panel? Does it have sound preferences?

---

### Post by lkjoel on 2011-07-28
Try Sound Troubleshooting in my signature

---

### Post by cavalier911 on 2011-07-28
Determine your sound device order:
```
cat /proc/asound/cards
```
Dell laptop with Logitech USB headset plugged in:
```
rj@lubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfebc000 irq 21
 **1 **[Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.2-1, full speed

```
```
sudo leafpad /etc/asound.conf
```
Set sound device **1** USB Headset as default:
```
defaults.ctl.card **1**
defaults.pcm.card **1**

```
File/Save/Quit
Reboot

If you use both soundcard/speakers and USB headset:
UDEV rule switch's default sound device when USB headsets are plugged in. Software producing sound must be restarted after USB is inserted/removed.
```
sudo leafpad /etc/udev/rules.d/00-local.rules 
```
```
KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"
```

File/Save/Quit

---

