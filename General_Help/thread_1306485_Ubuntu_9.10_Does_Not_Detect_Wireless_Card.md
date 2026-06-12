---
title: "Ubuntu 9.10 Does Not Detect Wireless Card"
date: 2009-10-30
forum: General Help
---

### Post by jtwhite on 2009-10-30
The last version worked fine with my wireless card. Now, it's not working at all.

What can I do?

I have a Dell Insprion 1525

---

### Post by jtwhite on 2009-10-30
Bump

---

### Post by HappyFeet on 2009-10-30
Do
```
lspci
```
and post the output here.

---

### Post by jtwhite on 2009-10-30
> **HappyFeet said:**
> Do
```
lspci
```
and post the output here.

Here's the output:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


```

---

### Post by prem1er on 2009-10-30
This card should be supported. Is the light on for the laptop that indicates that your wifi card is up?

---

### Post by jtwhite on 2009-10-30
Yes it is.

---

### Post by fooman on 2009-10-30
i have a hp-mini 1035nr that also has the bcm4312 wireless controller.

after installing 9.10 (netbook remix version)...the wireless was not working.  trying to enable it from the hardware drivers would not work,  even though it showed the driver as being enabled....it would not function.

reinstalling the "bcmwl-kernel-source" package (it was installed by default), followed by a reboot has fixed the issue for me.

i would suggest you try it....open a terminal and type or copy/paste the following:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```or if it is *not* installed already....try installing:

```
sudo apt-get install bcmwl-kernel-source
```hope that helps.  remember,  you may need a reboot afterwards.

EDIT:  oops,  there of course should be a "sudo" in front of each of those (added)...sorry.

---

### Post by jtwhite on 2009-10-30
> **prem1er said:**
> This card should be supported. Is the light on for the laptop that indicates that your wifi card is up?

Actually I just checked again and it's not lit up.

---

### Post by rcarroll215 on 2009-10-30
Try hitting Fn + F2 and see if the wifi light comes on.  I've had problems with the wifi LED's on Dell laptops with Ubuntu before, but I think the 1525's should work.

---

### Post by jtwhite on 2009-10-30
I just tried again and it seems to work.. I have no clue why it wasn't working before... Maybe it's because I installed what fooman said.

Thanks guys.

---

### Post by bhishan on 2009-10-30
> **jtwhite said:**
> The last version worked fine with my wireless card. Now, it's not working at all.

What can I do?

I have a Dell Insprion 1525

You need to find a wired connection first. After connecting to the wired connection install the ubuntu-restricted-extras from the software centre and then go to system>administration>hardware drivers and activate the drivers shown in the list. You should be good to go after that. Mine is Dell inspiron 1525 too. It took a while to figure out the problem.

Cheers

---

### Post by ghayl on 2010-11-23
Great fooman,
It worked for me too :)
Thanks.

---

