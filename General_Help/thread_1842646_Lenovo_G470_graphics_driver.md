---
title: "Lenovo G470 graphics driver"
date: 2011-09-11
forum: General Help
---

### Post by Alan502 on 2011-09-11
Hi,

I just bought a lenovo computer and installed ubuntu on it. However, the resolution is not showing properly and the ubuntu effects are the simplest ones (Do i need a graphics driver?). Here's the lspci:

```
alan@alan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```Thanks in advance :)

Edit: Im using ubuntu 10.04 64bit

---

### Post by www.rzr.online.fr on 2011-10-09
> **Alan502 said:**
> Hi,

I just bought a lenovo computer and installed ubuntu on it. However, the resolution is not showing properly 


Had this too , but after kernel upgrade it's ok

But I am unsure about 3D

Regards

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

