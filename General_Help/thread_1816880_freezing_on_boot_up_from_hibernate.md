---
title: "freezing on boot up from hibernate"
date: 2011-08-02
forum: General Help
---

### Post by bobthesob on 2011-08-02
Hi!
My laptop freezes when I boot it after a hibernate. 
The ubuntu logo shows and then there's a text that says
"trying to resume from /dev/disk/by-uuid/8879ds7e-f2e1 (then it continues with a lot of numbers and slashes)"

And then nothing happens. 

Any suggestions?

//Bob

---

### Post by cogier on 2011-08-02
You don't indicate which version of Ubuntu you are using or which computer you are using, this will not help you get a useful answer. 

There has always been the odd issue with Hibernation so a simple solution is to avoid it. A decent computer will boot Ubuntu in 15 to 45 seconds so is it necessary?

---

### Post by bobthesob on 2011-08-02
> **cogier said:**
> You don't indicate which version of Ubuntu you are using or which computer you are using, this will not help you get a useful answer. 

There has always been the odd issue with Hibernation so a simple solution is to avoid it. A decent computer will boot Ubuntu in 15 to 45 seconds so is it necessary?


Well the issue isn't ome I had before. Been running ubuntu for a year and then it just happened. 

I have a Samsung N310

Here's the specifics
[HTML]system      Notebook
/0                                bus         N310
/0/0                              memory      102KiB BIOS
/0/4                              processor   Intel(R) Atom(TM) CPU N270   @ 1.6
/0/4/5                            memory      64KiB L1 cache
/0/4/6                            memory      512KiB L2 cache
/0/4/1.1                          processor   Logical CPU
/0/4/1.2                          processor   Logical CPU
/0/e                              memory      1GiB System Memory
/0/e/0                            memory      1GiB SODIMM DDR2 Synchronous 533 M
/0/e/1                            memory      SODIMM DDR2 Synchronous 533 MHz (1
/0/100                            bridge      Mobile 945GME Express Memory Contr
/0/100/2                          display     Mobile 945GME Express Integrated G
/0/100/2.1                        display     Mobile 945GM/GMS/GME, 943/940GML E
/0/100/1b                         multimedia  N10/ICH 7 Family High Definition A
/0/100/1c                         bridge      N10/ICH 7 Family PCI Express Port 
/0/100/1c/0            wlan0      network     AR5001 Wireless Network Adapter
/0/100/1c.2                       bridge      N10/ICH 7 Family PCI Express Port 
/0/100/1c.2/0          eth0       network     88E8040 PCI-E Fast Ethernet Contro
/0/100/1d                         bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.1                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.2                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.3                       bus         N10/ICH 7 Family USB UHCI Controll
/0/100/1d.7                       bus         N10/ICH 7 Family USB2 EHCI Control
/0/100/1e                         bridge      82801 Mobile PCI Bridge
/0/100/1f                         bridge      82801GBM (ICH7-M) LPC Interface Br
/0/100/1f.2            scsi0      storage     82801GBM/GHM (ICH7 Family) SATA ID
/0/100/1f.2/0.0.0      /dev/sda   disk        160GB SAMSUNG HM160HI
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      146GiB EXT4 volume
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      2997MiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5  volume      2997MiB Linux swap / Solaris parti
/0/100/1f.3                       bus         N10/ICH 7 Family SMBus Controller
/1                                power       Intel Corporation
/2                                system      [/HTML]

And I'm running Ubuntu 11.04

---

### Post by bobthesob on 2011-08-02
And yes it's necessary. I don't want to close all my programs and documents when I need to go away for a while. And I think it's a feature that Ubuntu should be able to provide.

---

