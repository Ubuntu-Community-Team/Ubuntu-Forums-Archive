---
title: "SD Card reader undetected? Sadface."
date: 2010-12-06
forum: General Help
---

### Post by xCasualty on 2010-12-06
I have all of my music on an SD card so it doesn't take up space on my hard drive. I put it into my SD card reader and ubuntu is all like, "gtfo doesn't exist." Help please? haha

---

### Post by xCasualty on 2010-12-06
```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

```

---

### Post by NeXTWay on 2011-01-04
Hi, sorry for bumping this old thread but I'd like to share with you the driver I've found.

1)Download the file I've attached to this post
2)Check it's md5sum (96f435f5439d209618fc36d68c3fa03d)
3)Go to the downloads folder and untar ```
tar xfv rts*.gz
```
4)Compile ```
cd rts_pastor && make clean && ./configure && make && sudo make install
```
5)depmod ```
sudo depmod
```
6)Reboot: everything should work fine ^^

EDIT: Forgot to mention that the file I've uploaded here is just my installation directory. You could have problem with permissions while compiling. If so
```
sudo chmod a+xwr *
```
inside the directory and then try to re-compile.

I use Kernel26 on Arch and this driver works fine. Never tried on Ubuntu Kernel but I guess it should run nicely ^^

---

