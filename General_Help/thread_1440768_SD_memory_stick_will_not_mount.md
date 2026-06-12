---
title: "SD memory stick will not mount"
date: 2010-03-27
forum: General Help
---

### Post by dwhitney67 on 2010-03-27
A few months ago (circa Xmas time), with Ubuntu 9.10 I was able to insert my SD Memory Card into my laptop, and it would be auto-mounted.

Tonight I tried and no joy... the card is not mounted.  Is my system missing a kernel module, or is it possible that the appropriate module is not being loaded by the kernel?

I am using version 2.6.31-20-generic of the Linux (err, Ubuntu) kernel.

Here's my 'lspci' listing:
```

$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller

```

Can anyone help?

P.S.  This is the output from /var/log/messages:
```

Mar 27 22:31:56 iceland kernel: [915230.835771] mmc0: problem reading switch capabilities, performance might suffer.
Mar 27 22:31:56 iceland kernel: [915230.837872] mmc0: new SD card at address 0002
Mar 27 22:31:56 iceland kernel: [915230.838134] mmcblk0: mmc0:0002       974 MiB 
Mar 27 22:31:56 iceland kernel: [915230.838259]  mmcblk0: p1

```

---

### Post by paxmark1 on 2010-04-02
bump please.  

I can acess usb items via 2.6.31-19-generic but not via 2.6.31-20-generic.  SD memory stick flaky and received a longer new name. unison would not synchronize a pre-existing preference. XD picture card  not seen via card reader.  USB HDD not seen.  

mobo ASUS P5KPL-VM  4GB RAM

2.6.31-20-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux  

/proc$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)


tia 

peace mark

---

### Post by celem on 2010-04-02
Read [http://ubuntuforums.org/showthread.php?t=1306577]("http://ubuntuforums.org/showthread.php?t=1306577")

Worked for me.

---

### Post by dwhitney67 on 2010-04-02
Yes, it seems to have worked for me too.  I de-installed **brasero**, then installed **gnome-mount** and **gnome-volume-manager** (even though the other guy said it wasn't necessary).

Initially, my system still would not auto-mount the SD memory card, but after a logout and then a login (to get gnome to re-spin it's wheels), the card was auto-mounted and f-spot was auto-launched to read the device.

Let's hope this is a permanent solution.

---

### Post by paxmark1 on 2010-04-02
didn't think it would work but

aptitude install gnome-mount 

fixed the upgrade to 2.6.31-20-generic's not wanting to automount  usb items.

Strange, it also fixed the glitch 2.6.31-20-generic did to my mplayer 2:1.0~rc3+svn20090426-1ubuntu10.1 and compiled smplayer not playing sound after going to 2.6.31-20   

Thanks  If this fixes it for original poster also, please mark as SOLVED

---

### Post by Bernard Hurley on 2010-05-12
In lucid a better solution might be might be to just remove the package "usbmount" as suggested in:
[http://ubuntuforums.org/showthread.php?t=1468755](http://ubuntuforums.org/showthread.php?t=1468755)

Since lucid doesn't have the package gnome-volume-manager, if it is in your startup apps, you might as well remove it so that gnome doesn't waste time looking for it!

---

### Post by nolasco_fernando on 2011-10-04
hi all, i have a problem reading my memory stick "Sony Memory PRO Duo". Im using Ubuntu 10.10, running on a HP Pavillion. USB flash drives is automatically mounted, so theres no problem about it, but memory stick is an issue. i check /dev/ if there is a device added each time i insert the stick, hoping to mount manually since automount does not work. but there are no added devices. i check pci buses using lspci and ubuntu can read this which is i think the same pci bus i found when i run windows

(--output ommitted--)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

i think the result show it identified the pci bus and then i check the loaded module using lsmod

(--output omiited--)
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
(--output omitted--)

i think this is related to the device i want to read.

i really dont know what else to do, still cant figure what is wrong. 

hope someone can help, thanks.

---

