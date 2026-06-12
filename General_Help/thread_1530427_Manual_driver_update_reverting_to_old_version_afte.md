---
title: "Manual driver update reverting to old version after boot"
date: 2010-07-13
forum: General Help
---

### Post by mustainefan on 2010-07-13
[LEFT]Hi wonderful community!
[/LEFT]
 
I'm running into some problems here. I'm trying to setup bonding on two GigE cards. Things seem find but when I test out a couple different file transfers on samba, I'm getting a kernel panic. In the process I'm trying to update the e1000e driver (Intel 82574L). The problem I'm having with this is after I reboot, the old e1000e driver is getting loaded.

Here's some background. Installed is 10.04, upgraded and dist-upgraded:
```
$ uname -r
Linux SERVERNAME 2.6.32-23-server #37-Ubuntu SMP Fri Jun 11 09:11:11 UTC 2010 x86_64 GNU/Linux
``````
$ lspci | grep Ethernet
02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```Below I note "1.0.2-k2" for driverversion.
```
$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: 6c:f0:49:06:ff:22
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-0 latency=0 link=yes multicast=yes port=twisted pair slave=yes speed=1GB/s
       resources: irq:16 memory:e9080000-e909ffff memory:e9000000-e907ffff ioport:b000(size=32) memory:e90a0000-e90a3fff memory:ec200000-ec23ffff(prefetchable)

```So I downloaded and updated e1000e to version 1.1.19 by following their directions, first backing up the old driver:
```
$ sudo mv /lib/modules/2.6.32-23-server/kernel/drivers/net/e1000e/e1000e.ko backup
$ cd e1000e-1.1.19/src
$ sudo make install
make -C /lib/modules/2.6.32-23-server/build SUBDIRS=/home/HOME/e1000e-1.1.19/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-server'
  CC [M]  /home/HOME/e1000e-1.1.19/src/netdev.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/ethtool.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/param.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/e1000_82571.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/e1000_ich8lan.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/e1000_80003es2lan.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/e1000_mac.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/e1000_nvm.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/e1000_phy.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/e1000_manage.o
  CC [M]  /home/HOME/e1000e-1.1.19/src/kcompat.o
  LD [M]  /home/HOME/e1000e-1.1.19/src/e1000e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/HOME/e1000e-1.1.19/src/e1000e.mod.o
  LD [M]  /home/HOME/e1000e-1.1.19/src/e1000e.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-server'
gzip -c ../e1000e.7 > e1000e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.32-23-server -name e1000e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.32-23-server -name e1000e.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000e.ko /lib/modules/2.6.32-23-server/kernel/drivers/net/e1000e/e1000e.ko
/sbin/depmod -a || true
install -D -m 644 e1000e.7.gz /usr/share/man/man7/e1000e.7.gz
man -c -P'cat > /dev/null' e1000e || true
e1000e.
```And then I uninstall the old one, install the new one per README file
```
$ sudo rmmod e1000e
$ sudo modprobe e1000e
```After restarting networking, my lshw is now (note that driverversion=1.1.19-NAPI now):
```
$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: 6c:f0:49:06:ff:22
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.1.19-NAPI duplex=full firmware=1.8-0 latency=0 link=yes multicast=yes port=twisted pair slave=yes speed=1GB/s
       resources: irq:16 memory:e9080000-e909ffff memory:e9000000-e907ffff ioport:b000(size=32) memory:e90a0000-e90a3fff memory:ec200000-ec23ffff(prefetchable)
```So here comes the problem and I must be missing something here - after I reboot, the old 1.0.2-k2 driverversion is loaded.
```
$ sudo reboot
$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: 6c:f0:49:06:ff:22
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-0 latency=0 link=yes multicast=yes port=twisted pair slave=yes speed=1GB/s
       resources: irq:16 memory:e9080000-e909ffff memory:e9000000-e907ffff ioport:b000(size=32) memory:e90a0000-e90a3fff memory:ec200000-ec23ffff(prefetchable)
```What am I missing?

Thanks,
mustainefan

---

### Post by mustainefan on 2010-07-15
After some tinkering I think I've found why the wrong e1000e driver was loading after booting. The driver in initrd.img was being loaded. 

Feel free to correct this if it's not-so-elegant. I unzipped my current initrd.img file, replaced the older e1000e with the newer one I compiled, and the zipped it back up.

I logged onto root for this...
```
$ sudo su -
# mkdir myinitrd && cd myinitrd
# gzip -dc /boot/initrd.img-2.6.32-23-server |cpio -i
# rm lib/modules/2.6.32-23-server/kernel/drivers/net/e1000e/e1000e.ko
# cp /lib/modules/2.6.32-23-server/kernel/drivers/net/e1000e/e1000e.ko \
     lib/modules/2.6.32-23-server/kernel/drivers/net/e1000e/
# find . |cpio -o -H newc | gzip -9 > /boot/initrd.img-2.6.32-23-server-custom
```I then edited grub.cfg and added a new entry with my new initrd.img-2.6.32-23-server-custom file. Now when I boot lshw reports driverversion=1.1.19-NAPI.

Now whether this fixes my ultimate problem is yet to be determined....

---

### Post by stoon on 2011-09-05
I found running update-initramfs with the correct kernel module installed/loaded did the trick too.

---

### Post by _bsd on 2011-09-20
>I found running update-initramfs with the correct kernel module installed/loaded did the trick too.

stoon, Thank you, Thank you, Thank you!

None of the obvious search strings were taking me to a proper solution. I built the source from Intel and it works but after each boot I had to manually rmmod e1000e; modprobe e1000e; to get the module loaded. A circumnavigational search lead to your answer which explains the problem and, for now, a solution. :p

---

