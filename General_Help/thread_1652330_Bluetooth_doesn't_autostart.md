---
title: "Bluetooth doesn't autostart"
date: 2010-12-24
forum: General Help
---

### Post by coderpp on 2010-12-24
I use ubuntu 10.10 x64. Bluetooth dosn't autostart. I can start it pressing Fn + F3.

---

### Post by matt_symes on 2010-12-24
Hi

i don't use 10.10x64 so i might be completely wrong here, but...

When you say bluetooth does not start are you talking about the service or the applet.

Kind regards

---

### Post by coderpp on 2010-12-24
Both.

Maybe this isn't ubuntu porblem?

I have acer aspire 3810t, bluetooth autostart worked on windows xp or vista and ubuntu 9.04, but it didn't work un windows 7 and it doesn't work on ubuntu 10.10. On all systems bluetooth was configured for autostart.

---

### Post by matt_symes on 2010-12-24
Hi

So in system->start up applications is bluetooth manager selected to start at start up? 

Also at a terminal type

```
sudo apt-get install rcconf
```

enter password as usual and then type

```
rcconf
```

is the bluetooth start bluetoothd option selected?

Also at a terminal if you type

```
/etc/init.d/bluetooth status
```

it says * bluetooth is not running ? (obviously before you have tried to start it with your key press)

> I can start it pressing Fn + F3

This starts the service and the applet in 10.10 but in < 10.10 you did not need to do this to start bluetooth?

Were your previous Ubuntu versions also 64bit ?

Kind regards

---

### Post by coderpp on 2010-12-24
Hi,

Bluetooth manager is selected to start at start up.

bluetoothd is selected.

> it says * bluetooth is not running ?
No, it says * bluetooth is running
But i have manualy started it with Fn + F3.

> This starts the service and the applet in 10.10 but in < 10.10 you did not need to do this to start bluetooth?
In Ubuntu 10.04 bluetooth started with system.

> Were your previous Ubuntu versions also 64bit ?
Yes.

---

### Post by matt_symes on 2010-12-24
Hi

Right i see. That is quite interesting as the FN + F3 key is the key combination used to enable bluetooth, in the same way that FN + F4 is hibernate and FN + F8 is toggle mute. 

So, in a way, the question is why was FN + F3 not working < 10.10 as that is what that keypress combination is for.

Its current behaviour in 10.10 seems to be the expected behaviour.

I might not be the best person to help you, maybe others will know.

What i will do is some research to see if i can find an answer.

EDIT: You have a acer aspire 3810t and i am writing this on an acer aspire also.

Kind regards

---

### Post by coderpp on 2010-12-24
> So, in a way, the question is why was FN + F3 not working < 10.10 as that is what that keypress combination is for.

No! Key combination works on all systems. :) On previus ubuntu version i didn't use this key combination, because bluetooth started automatically.

But now, i need manualy turn it on. :( And that is the problem.

Edit:
Just tried ubuntu 11.04 x64. It dosn't autostart bluetooth too. :( I will download 32 bit version and check if there problem exists too

---

### Post by matt_symes on 2010-12-24
Hi

> On previus ubuntu version i didn't use this key combination, because bluetooth started automatically.

Yes, that was kind of the point i was trying to make ;)

Anyhow, lets try something.

Reboot the PC. Don't enable your bluetooth. Open a terminal and type

```
rfkill list
```

Copy the results somewhere. Enable your bluetooth. Enter the same command again

```
rfkill list
```

Post both sets of results back on this thread.

Kind regards

---

### Post by coderpp on 2010-12-24
List 1, before turning bluetooth on:
> coderpp@coderpp-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


List 2, after turning on bluetooth:
> coderpp@coderpp-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


---

### Post by matt_symes on 2010-12-24
Hi

Thats a shame. That could have been a simple fix.

Anyhow, another reboot first. After the reboot don't enable bluetooth and type at the terminal.

```
dmesg | grep -i bluetooth
```

This may or may not return results. If it does copy then as before. Then start bluetooth and type

```
dmesg | grep -i bluetooth
```

again and post the results back. If there are no results from the first try the please tell me that.

Kind regards

---

### Post by coderpp on 2010-12-24
Ok, i will do it after ~ 30 - 40 minutes, because i am downloading 32 bit version.

---

### Post by matt_symes on 2010-12-24
Hi

No problem. I am going to sleep soon anyway (its late here), but post the results anyway as i will look tomorrow morning.

What i am going to do is download the 64bit 10.10 and install it on a spare partition i have for these kind of situations. I don't have an inbuilt bluetooth card but i do have a USB one.

I am going to see if i can recreate the problem you are having and if i can we can both track down what has changed faster (hopefully).

Good night.

Kind regards

---

### Post by coderpp on 2010-12-24
> coderpp@coderpp-laptop:~$ dmesg | grep -i bluetooth
coderpp@coderpp-laptop:~$ dmesg | grep -i bluetooth
[  117.159997] Bluetooth: Core ver 2.15
[  117.160054] Bluetooth: HCI device and connection manager initialized
[  117.160058] Bluetooth: HCI socket layer initialized
[  117.167784] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  117.221876] Bluetooth: L2CAP ver 2.14
[  117.221880] Bluetooth: L2CAP socket layer initialized
[  117.228005] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  117.228009] Bluetooth: BNEP filters: protocol multicast
[  117.233590] Bluetooth: SCO (Voice Link) ver 0.6
[  117.233593] Bluetooth: SCO socket layer initialized
[  117.343316] Bluetooth: RFCOMM TTY layer initialized
[  117.343324] Bluetooth: RFCOMM socket layer initialized
[  117.343327] Bluetooth: RFCOMM ver 1.11
[  117.505549] Bluetooth: HIDP (Human Interface Emulation) ver 1.2


Results only on second try.

Ubutu 10.10 32bit dosn't autostart bluetooth too, i tried live USB and cheked autostart session, there bluetooth manager was enabled.

---

### Post by efflandt on 2010-12-24
Was that dmesg output before or after you manually turned it on with Fn+F3?  That output is similar to what I see when plugging in a Bluetooth USB dongle, and the Bluetooth applet comes up in the top panel at that point.

Bluetooth manager is started at boot, but the applet only comes up when the system recognizes a bluetooth device.  Did you have to install any driver for bluetooth to work?  Maybe the hardware is not recognized during boot, so a module is not starting automatically.  You might check your BIOS settings to see if anything there has it disabled during boot.

For example when I installed Broadcomm STA for a wireless card live iso on USB with persistent data, I had to manually load the module (or from a script) before it was recognized.  Although, for a regular install, the module loaded automatically.

What does **sudo lspci -v** show about your bluetooth device?

---

### Post by coderpp on 2010-12-25
> Was that dmesg output before or after you manually turned it on with Fn+F3? That output is similar to what I see when plugging in a Bluetooth USB dongle, and the Bluetooth applet comes up in the top panel at that point.

That was after i manually turned on.

> Bluetooth manager is started at boot, but the applet only comes up when the system recognizes a bluetooth device. Did you have to install any driver for bluetooth to work? Maybe the hardware is not recognized during boot, so a module is not starting automatically. You might check your BIOS settings to see if anything there has it disabled during boot.

No, i didnt install any driver.

> What does sudo lspci -v show about your bluetooth device? 

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0a <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, fast devsel, latency 0
	Memory at e2400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 30e0 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 30c0 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at e4505c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: e3500000-e44fffff
	Prefetchable memory behind bridge: 00000000e0400000-00000000e13fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0229
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: e2500000-e34fffff
	Prefetchable memory behind bridge: 00000000e1400000-00000000e23fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0229
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 30a0 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3080 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 3060 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3040 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at e4505800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 0229

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
	I/O ports at 3108 [size=8]
	I/O ports at 311c [size=4]
	I/O ports at 3100 [size=8]
	I/O ports at 3118 [size=4]
	I/O ports at 3020 [size=32]
	Memory at e4505000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/16 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: medium devsel, IRQ 11
	Memory at e4506000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 3000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: fast devsel, IRQ 11
	Memory at e4504000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3

01:00.0 Network controller: Intel Corporation WiFi Link 5100
	Subsystem: Intel Corporation WiFi Link 5100 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e3500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-22-fb-ff-ff-72-4b-32
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at e2500000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 1000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [180] Device Serial Number ff-23-30-5a-00-1e-33-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c


I checked live usb with ubuntu 9.10 x64 system, bluetooth was started automatically.

Edit: On Ubuntu 10.04.1 32bit system bluetooth autostarts.

---

### Post by coderpp on 2010-12-26
Can anybody help me solve this problem?

---

### Post by coderpp on 2010-12-26
Installed two kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).

First: v2.6.37-rc2-maverick
Second: v2.6.32.27-lucid

With first kernel bluetooth autostart didn't work, bet with second kernel bluetooth started with system. 

So, problem is with kernel, not ubuntu, right?

I don't want use old kernel, so what can i do, to get it working in newer kernels?

---

### Post by marcuskall on 2011-04-04
I have the same problem with my acer 4810T and 11.04

I added the lines: 
rfkill block bluetooth
rfkill unblock bluetooth

to my /etc/rc.local and now bluetooths autostarts!

---

### Post by coderpp on 2011-04-06
Still doesn't work :(

---

