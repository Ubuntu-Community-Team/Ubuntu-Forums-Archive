---
title: "DotS"
date: 2009-10-17
forum: General Help
---

### Post by format C: /q on 2009-10-17
Hello out there. 
Im new to the whole Linux/Ubuntu world and its realy nice that there are people like all of you out there to make and helpout for free like this. 
 
Now the reson im entering a post here. 
I installed ubuntu on my netbook and then moved on whit the notebook edition. 
My netbook is a "Packard Bell DotS".
I works quite well, starts upp and all, but the problem is that the network dont work at all, not the wired or the wireless. 
And this is a big problem it seems, its like i need network to fix my problem ?
I have tried ALL of the fixes regarding Atheros "AR5B95" and "AR8132" i found on this forum but nothing seems to work. 
 
So my question is: can someone fix so that DotS is included in the Netbook Edition of ubuntu ?

---

### Post by ugm6hr on 2009-10-17
If you copy and paste onto a USB the output from:
```
lspci
lshw -class network
```

---

### Post by format C: /q on 2009-10-17
[SIZE=4][COLOR=darkorange]lspci results:[/COLOR][/SIZE]
 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
 
[SIZE=4][COLOR=sandybrown]lshw -class network results:[/COLOR][/SIZE]

RNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:01:00.0"]pci@0000:01:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:01:91:71:13:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by ugm6hr on 2009-10-17
Assuming Jaunty / 9.04 use:
Wired solution: [http://ubuntuforums.org/showthread.php?p=7821376#post7821376](http://ubuntuforums.org/showthread.php?p=7821376#post7821376)

Once online with wired, hopefully, wifi will be easier to solve.

Wifi:
```
sudo apt-get update 
sudo apt-get install linux-backports-modules-$(uname -r)
```
From: [http://ubuntuforums.org/showthread.php?t=1244686](http://ubuntuforums.org/showthread.php?t=1244686)

---

### Post by format C: /q on 2009-10-17
wow it workes like a charm !
many thanx ugm6hr!  =D>

---

### Post by ugm6hr on 2009-10-17
Given it is a NetBook, I presume you will be predominantly wifi.

However, be aware that the wired driver installation process will need to be repeated each time you upgrade your kernel.

Just change the line:
```
$ cd /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e/
```
to
```
$ cd /lib/modules/$(uname -r)/kernel/drivers/net/atl1e/
```

i.e., starting at the directory containing the untarred (uncompressed) driver:
```
cd src
make
sudo make install
cd /lib/modules/$(uname -r)/kernel/drivers/net/atl1e/
sudo insmod ./atl1e.ko
```

Hopefully, that should work.

---

