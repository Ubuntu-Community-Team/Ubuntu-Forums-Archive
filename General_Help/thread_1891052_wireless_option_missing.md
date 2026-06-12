---
title: "wireless option missing?"
date: 2011-12-04
forum: General Help
---

### Post by devapea on 2011-12-04
sorta newbie trying to get wireless working on laptop. recently replaced windows with new ubuntu version. Frustrating. network icon shows no wireless option.  Can not create new wireless connection when I edit connections. (maybe I dont have permission?) 

iwconfig shows only lo and etho0 with no wireless connection.  

I have installed ndiswrapper along with windows drivers inf.

still stumped.  Any help ideas appreciated thank you!

---

### Post by idoitprone on 2011-12-04
should i start this thread by asking for the wireless card?

```
lspci -v
```or say try to use

```
ifconfig wlan0 up
```

---

### Post by devapea on 2011-12-05
amy@AAdams:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 80200000-803fffff
	Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: dfd00000-dfdfffff
	Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfa00000-dfcfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: df900000-df9fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Device 01cd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	Subsystem: Dell Device 01cd
	Flags: medium devsel, IRQ 4
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Inspiron 9400 Laptop
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at df9fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at df9fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Device 01cd
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at df9fd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: Dell Device 01cd
	Flags: medium devsel, IRQ 11
	Memory at df9fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
	Subsystem: Dell Device 01cd
	Flags: medium devsel, IRQ 18
	Memory at df9fd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: r852
	Kernel modules: r852

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb

amy@AAdams:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

---

### Post by devapea on 2011-12-05
thank you for your help btw!

---

### Post by westie457 on 2011-12-05
Hi the needed drivers or you card vary according to the version of Ubuntu you are running.

Post that and you will be informed of the next steps.

Thankyou

---

### Post by devapea on 2011-12-05
running the latest ver. 11.10

when trying to identify broadcom card/driver I get this:

amy@AAdams:~$ lspci -vvnn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
amy@AAdams:~$ 

looks like it doesnt see any wireless card. Am I right?

---

### Post by westie457 on 2011-12-05
The card has been seen and is a b4311 chip, the same as in my laptop.
have you looked at 'Additional Drivers' to find out if the driver needs activating. An ethernet cable is required for this to be installed followed by a reboot to write to the system files.

After the reboot click on the network manager icon to see any available networks, select yours enter any details when prompted and you should away.

Any problems post back here and we will get tough with the sucker.

---

### Post by devapea on 2011-12-05
Yes I had done that before and installed the sta propriety drivers and also windows drivers thru ndiswrapper which still did not fix the problem. I thought if I could create a new wireless connection that might help but it wont give me permission.  Any ideas? Thank you guys for continued help.

---

### Post by idoitprone on 2011-12-05
> **devapea said:**
> amy@AAdams:~$ lspci -v


0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules:** wl, ssb**

amy@AAdams:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

Why is there two kernel modules for the boardcom things or watever
I believe the modules are conflicting each other

```
modprobe -r ssb
```If that does not work the re add the module and remove the other one

```
modproble -r wl
modprobe ssb
```I believe it is ```
ifconfig eth1 up
``` up not wlan0 for boardcomm (infamous of history of bad linux support)

[http://www.linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy](http://www.linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy)

---

### Post by bkratz on 2011-12-05
This _will_ work for both 11.04 and 11.10

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by devapea on 2011-12-05
amy@AAdams:~$ modprobe -r ssb
FATAL: Module ssb is in use.
amy@AAdams:~$ modproble -r wl
No command 'modproble' found, did you mean:
 Command 'modprobe' from package 'module-init-tools' (main)
modproble: command not found
amy@AAdams:~$ modprobe -r wl
FATAL: Error removing wl (/lib/modules/3.0.0-13-generic/updates/dkms/wl.ko): Operation not permitted
amy@AAdams:~$ modprobe ssb
amy@AAdams:~$ sudo modprobe -r ssb
[sudo] password for amy: 
FATAL: Module ssb is in use.
amy@AAdams:~$ modprobe -r ssb
FATAL: Module ssb is in use.
amy@AAdams:~$ ifconfig eth1 up
SIOCSIFFLAGS: Permission denied
amy@AAdams:~$ sudo ifconfig eth1 up
amy@AAdams:~$ sudo modprobe -r ssb
FATAL: Module ssb is in use.
amy@AAdams:~$ sudo modprobe -r wl
amy@AAdams:~$ sudo modprobe ssb

amy@AAdams:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
amy@AAdams:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amy@AAdams:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,367 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 167009 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
amy@AAdams:~$ sudo rm /etc/modprobe.d/broadcom-sta-common.conf
rm: cannot remove `/etc/modprobe.d/broadcom-sta-common.conf': No such file or directory
amy@AAdams:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory
amy@AAdams:~$ 


hmmmm....I will try to reboot.

---

### Post by devapea on 2011-12-05
Well that all worked after I rebooted.  Your right there must of been a conflict there.  Thankyou guys very much for your help.  Another Ubuntu success story!

---

### Post by bkratz on 2011-12-06
> **devapea said:**
> Well that all worked after I rebooted.  Your right there must of been a conflict there.  Thankyou guys very much for your help.  Another Ubuntu success story!

Congratulations and enjoy!

---

