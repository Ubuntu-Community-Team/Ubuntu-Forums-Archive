---
title: "fresh Kubuntu 11.04 wired internet problems"
date: 2011-08-21
forum: General Help
---

### Post by ADani on 2011-08-21
Hello, I'm having problems with a Kubuntu 11.04 install I made for dual boot
Motherboard: Gigabyte H61M-D2P-B3
Processor: Intel i3-2100 3.1GHz
Video: Nvidia GeForce 8800 GTS
Memory: Kingston 2X2GB DDR3.

The wired internet comes and goes, its laggy (actually the whole system feels that way). Usually unchecking and then checking the "Enable networking" button successfully reconnects. I had to try several times to "reload" on Synaptic because the connection kept dropping, and Gdebi package installer kills it every time I try to install Chrome: “Could not download all the required files. Please check your internet connection or installation medium”

Trying with Yakuake left a broken dependency:

```
dani@daniela:~/Downloads$ sudo dpkg -i google-chrome-stable_current_i386.deb
[sudo] password for dani:
Selecting previously deselected package google-chrome-stable.
(Reading database ... 95396 files and directories currently installed.)
Unpacking google-chrome-stable (from google-chrome-stable_current_i386.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
google-chrome-stable depends on libnspr4-0d (>= 4.7.3-0ubuntu1~); however:
Package libnspr4-0d is not installed.
google-chrome-stable depends on libnss3-1d (>= 3.12.3); however:
Package libnss3-1d is not installed.
google-chrome-stable depends on libcurl3; however:
Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
google-chrome-stable

``` lshw -C network:
```
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 06
serial: 50:e5:49:20:fb:86
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:41 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff
``` lspci -nn:
```
 00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation 6 Series Chipset Family LPC Controller [8086:1c5c] (rev 05)
00:1f.2 IDE interface [0101]: Intel Corporation 6 Series Chipset Family 4 port SATA IDE Controller [8086:1c00] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
00:1f.5 IDE interface [0101]: Intel Corporation 6 Series Chipset Family 2 port SATA IDE Controller [8086:1c08] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [GeForce 8800 GTS] [10de:0193] (rev a2)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
04:00.0 PCI bridge [0604]: Device [1b21:1080] (rev 01)

``` Thanks in advanced

---

### Post by ADani on 2011-09-20
I don't know how but it solved itself, maybe the connection lasted long enough to download some update that solved it.

---

### Post by bkratz on 2011-09-20
> **ADani said:**
> I don't know how but it solved itself, maybe the connection lasted long enough to download some update that solved it.

Just out of curiosity ( don't mess with success!)

You might just want to check and see if your modules  (lsmod ) and see if it now shows that you are using [FONT=monospace]the driver R8168 instead of R8169 which you had as shown on your lshw -C network command.  The correct one for your card "[/FONT]product: RTL8111/8168B PCI Express Gigabit Ethernet controller" is the r8168 which perhaps was upgraded sometime.

---

### Post by ADani on 2011-09-20
I'm afraid it's still R1869

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:20:fb:86
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff

```

And don't worry, I won't mess with it unless it stops working ;)

---

### Post by ADani on 2011-10-11
To bkratz: after you made me notice my driver was the wrong one
> You might just want to check and see if your modules (lsmod ) and see if it now shows that you are using the driver R8168 instead of R8169 which you had as shown on your lshw -C network command. The correct one for your card "product: RTL8111/8168B PCI Express Gigabit Ethernet controller" is the r8168 which perhaps was upgraded sometime.
and after realizing my intenet connection was better but was still dropping and reconnecting constantly, I looked into it and found how to install the correct driver here:
[]("http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/")
[http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/]("http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/")

and, after that didn't worked very well, here:
[http://www.makeinstall.es/2011/06/problemas-con-realtek-rtl81118168b.html](http://www.makeinstall.es/2011/06/problemas-con-realtek-rtl81118168b.html)

Finally I think its really solved!

```
description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:20:fb:86
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8168** driverversion=8.025.00-NAPI duplex=full ip=192.168.0.13 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff

```

thanks for your comment, it helped me solve the whole thing.

---

### Post by bkratz on 2011-10-11
> **ADani said:**
> To bkratz: after you made me notice my driver was the wrong one

and after realizing my intenet connection was better but was still dropping and reconnecting constantly, I looked into it and found how to install the correct driver here:

[http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/](http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/)

and, after that didn't worked very well, here:
[http://www.makeinstall.es/2011/06/problemas-con-realtek-rtl81118168b.html](http://www.makeinstall.es/2011/06/problemas-con-realtek-rtl81118168b.html)

Finally I think its really solved!

```
description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:20:fb:86
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8168** driverversion=8.025.00-NAPI duplex=full ip=192.168.0.13 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff

```thanks for your comment, it helped me solve the whole thing.


Sure am glad it helped you!

---

### Post by ADani on 2011-10-14
One annoying thing though, the wrong driver r8169 keeps getting used every time I restart the PC. The instructions I used said to remove and blacklist that driver:
> 
Remove the r8169 module from the linux kernel.
# rmmod r8169

Finally, blacklist the r8169 driver add the following to /etc/modprobe.d/blacklist.conf:
#blacklist r8169 driver
blacklist r8169

which I did, but it keeps reappearing every time I restart. Making me do the whole uninstall/reinstall the correct driver all over again.
Any ideas?

---

### Post by AndresChort on 2011-10-20
This might help:
[http://ubuntuforums.org/showpost.php?p=11213498&postcount=21](http://ubuntuforums.org/showpost.php?p=11213498&postcount=21)

---

