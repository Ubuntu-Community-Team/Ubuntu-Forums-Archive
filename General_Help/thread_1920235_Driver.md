---
title: "Driver"
date: 2012-02-04
forum: General Help
---

### Post by holytree on 2012-02-04
ATI RADEON 512 MB X1550 Driver required for ubuntu 11.10

---

### Post by raja.genupula on 2012-02-04
open system settings -> Hardware -> Additional Drivers 
open that . it will show you if need to install any drivers and you can get from there .

give me output of ```
lspci
```

---

### Post by kc1di on 2012-02-04
This page may be of help:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by BC59 on 2012-02-04
> **kc1di said:**
> This page may be of help:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

This is a very good reference. But I think it doesn't mention the x-swat ppa:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install fglrx
Installing this ppa you have always the latest fglrx driver.

---

### Post by holytree on 2012-02-05
@BC59 - how will u know if the driver is installed??

---

### Post by holytree on 2012-02-05
@Raj--
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by BC59 on 2012-02-05
To see if the driver is installed:
```
fglrxinfo
```
If installed you'll see something like
> fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series       
OpenGL version string: 3.3.11399 Compatibility Profile Context


---

### Post by Yellow Pasque on 2012-02-05
fglrx dropped support for the X1550 a long time ago, so the previous suggestions in this thread are no good. Ubuntu comes with the open-source ati driver already installed. Use that. See the xorg-edgers ppa if you really want the latest ati open-source drivers.

---

### Post by holytree on 2012-02-06
fglrxinfo: command not found


now?? :/

---

### Post by Mark Phelps on 2012-02-06
> **holytree said:**
> fglrxinfo: command not found


now?? :/

Re-read post #8 -- there are NO ATI fglrx drivers that will work with your card and Ubuntu recent versions.  ATI dropped fglrx support for your card YEARS ago.

---

### Post by holytree on 2012-02-06
No Offence but will you please give a solution than trying to prove me wrong??

---

### Post by Yellow Pasque on 2012-02-06
> Ubuntu comes with the open-source ati driver **already installed**. **Use that.**

You're looking for a solution to a problem you don't have or you have a different problem that you haven't told us about.

---

