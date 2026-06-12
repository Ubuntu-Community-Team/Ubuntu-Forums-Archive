---
title: "how to use Bluetooth in Toshiba LapTop , ubuntu 9.10"
date: 2010-01-16
forum: General Help
---

### Post by rui.madaleno on 2010-01-16
Hi all,

this is my first post in the forums, please apologise if i've choose the wrong sub forum.

I'm using a Toshiba Satellite A200-21T LapTop with Ubuntu 9.10

I used to have dual boot with windows Xp but i shoot windows out (Sorry bill :) :) )

In windows i was able to use bluetooth with my nokia phone.

In ubuntu i'm totally puzzled how to configure it. I've read several post but i really need your help.

The wireless hardware button in the laptop is on. There is no option it the bios to turn off the bluetooth, so i'm sure that the machine is booting with bluetooth on.

i run this command in terminal:
```

ruival@ruimadlinux:~$ cat /var/log/dmesg | grep Blue*
[    0.380007] Bluetooth: Core ver 2.15
[    0.380012] Bluetooth: HCI device and connection manager initialized
[    0.380014] Bluetooth: HCI socket layer initialized
[    1.203541] Bluetooth: L2CAP ver 2.13
[    1.203542] Bluetooth: L2CAP socket layer initialized
[    1.203544] Bluetooth: SCO (Voice Link) ver 0.6
[    1.203546] Bluetooth: SCO socket layer initialized
[    1.203565] Bluetooth: RFCOMM TTY layer initialized
[    1.203568] Bluetooth: RFCOMM socket layer initialized
[    1.203569] Bluetooth: RFCOMM ver 1.11
ruival@ruimadlinux:~$ 
```But when i try hciconf i get no output:

```
ruival@ruimadlinux:~$ hciconfig
ruival@ruimadlinux:~$ 

```please help me configuring my bluetooth device

Best Regards

Rui Madaleno

---

### Post by rui.madaleno on 2010-01-16
And here's the output of the lspci command

> ruival@ruimadlinux:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
ruival@ruimadlinux:~$ 

---

### Post by rui.madaleno on 2010-01-16
here is the output of the lsusb command:

> ruival@ruimadlinux:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ruival@ruimadlinux:~$ 

---

