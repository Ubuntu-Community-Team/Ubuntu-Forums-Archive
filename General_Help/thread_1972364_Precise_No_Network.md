---
title: "Precise No Network"
date: 2012-05-03
forum: General Help
---

### Post by satish_j on 2012-05-03
Just installed Precise pangolin..And the network is not working,the icon on top right side is there but of diff type,pls see attached screenshot.
ALso,lspci detects N/w card as shown from below
```

satish@titan:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
**02:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)**
03:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
satish@titan:~$ 

```
Any ideas how to solve this?

---

### Post by Zvlwab on 2012-05-03
Is it about a wireless network? Check if the package modem-broadband-provider-info is installed
```
dpkg -l modem-broadband-provider-info
```

---

### Post by satish_j on 2012-05-04
> **Zvlwab said:**
> Is it about a wireless network? Check if the package modem-broadband-provider-info is installed
```
dpkg -l modem-broadband-provider-info
```

Nopes,this is wired connection.There was no eth0 in wired network list.I added it,but the 'last used' column is shown as 'never'.

---

### Post by satish_j on 2012-05-04
anyone pls help,here;s output of interfces file from my system
```

auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

---

### Post by satish_j on 2012-05-05
i must add here that mu inetrfaces file contained only foll after fresh installation
```

auto lo
iface lo inet loopback

```
Additional entries were inserted at time of configuring pppoe and sice then network interface eth0 is not getting detected
Any ideas now??

---

### Post by satish_j on 2012-05-06
confirmed..
If i configure pppoeconf,it updates /etc/network/interfaces file and after reboot,nm icon on top right panel stops detecting network card.
If the entries added by pppoeconf in above mentioned file are manually removed->& system rebooted,network starts working fine again.
Now,what should i do?Without ppoeconf,i cannot connect to internet.
A fresh latest ubuntu release installed on one of the drive but w/o internet makes it useless..
:(
Can anyone suggest alternate way to access internet?

---

### Post by satish_j on 2012-05-07
ok,got it working finally after a lot of digging around in google.
Foll setting in /etc/NetworkManager/NetworkManager.conf which was causing the problem:
```

managed=false

```
changed 'false' to 'true',restarted networking using
```

sudo /etc/init.d/network-manager restart

```
and now the nm applet is working fine with pppoe
..this post can be of benefit to someone in future..

---

