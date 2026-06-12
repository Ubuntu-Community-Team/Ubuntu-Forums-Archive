---
title: "So much for drivers"
date: 2009-09-19
forum: General Help
---

### Post by tpho2500 on 2009-09-19
I searched the forum for threads on HP dv6000 laptop threads and found all of the wireless drivers obsolete. I thought ubuntu would take care of installing drivers but I guess not. I'm trying to get to know linux more but so far Windows 7 has taken care of my drivers but why not Ubuntu?

If I install the wireless driver will ubuntu take care of the others? (sound, video, etc). If i have to install each driver manually then I will eliminate Ubuntu. 

My laptop:
HP Pavilion dv6000 (6838nr)

---

### Post by mike555 on 2009-09-19
Ubuntu has many drivers , but not all ....... but once you connect to the internet it might get them for you .... can you just plug to a router temporarily?

---

### Post by Bucky Ball on 2009-09-19
I have a HP dv6000 series laptop and it works fine, including wireless. What release of Ubuntu are you using and could you post the result of copy/pasting this in a terminal (Applications->Accessories):

```
lspci
```That will give us your wireless chipset/card. It should be a Broadcom and they are covered. Have you plugged an ethernet cable in and gotten all updates? That should identify a Broadcom card straight away (as mentioned in previous post, plug a cable in).

---

### Post by tpho2500 on 2009-09-19
No I cannot, I do not have any spare cables and prefer not to buy new ones just to get 1 driver. 

EDIT: one sec lemme boot into it

---

### Post by tpho2500 on 2009-09-19
My network controller: intel corp pro/wireless 4965 AG or AGN
ethernet: realtek semiconductor co. RTL8101E

---

### Post by Bucky Ball on 2009-09-19
This might help from post #8:

[http://ubuntuforums.org/showthread.php?t=843398](http://ubuntuforums.org/showthread.php?t=843398)

Do you mean RTL8101E? What does it say in:

```
lspci
```

... in a terminal? Post it here if you like.

---

### Post by tpho2500 on 2009-09-19
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Bucky Ball on 2009-09-19
Ta. Realtek RTL8101E/RTL8102E is what you're after then. Try the instructions for getting wireless up here:

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One)

---

### Post by tpho2500 on 2009-09-19
when i do ```
sudo ndisgtk
``` it says command not found

---

### Post by nothingspecial on 2009-09-19
Try installing linux-backports-modules-jaunty-generic.

Search for it in synaptic package manager

---

### Post by BarefootSoul83 on 2009-09-25
By the way...There were some recalls on some the HP laptops...it had to do with the battery...kinda dangerous...

[http://bpr.hpordercenter.com/hbpr/](http://bpr.hpordercenter.com/hbpr/)

---

