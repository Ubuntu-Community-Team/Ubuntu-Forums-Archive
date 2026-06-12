---
title: "WiFi problem"
date: 2011-11-03
forum: General Help
---

### Post by maxmiaggi on 2011-11-03
Hi there!

Well, I don't know whether this is the correct place to post this topic, so pardon me for that.

I have been using Ubuntu 10.04 LTS since two weeks. But there seems to be some problem with the wi-fi. After I login, the websites open perfectly for sometime (say 2-3 minutes), and after that, it says "Website not found" or "Server not found". And sometimes, they don't even open right after the login. I tried it with Firefox and Chromium browsers.

However, when I try it in Windows 7, everything works fine! There is absolutely no problem with the internet or wi-fi connectivity.

Anybody has any idea what the problem is?

---

### Post by irv on 2011-11-03
Why don't you give us more information about your system.
What Hardware your are using?
What Wifi card do you have installed?
Have you installed any drivers for your card?

This information will help and any other that you can provide.

---

### Post by 0121computers on 2011-11-03
If your running two internet seach engines at te same time they might be clashing for instance firefox and google chrome clash and so do internet explorer and firefox on some websites so if this is your problem stick to ether internet explorer which usaly works on nearly every site or google chrome is excelent if you are good on your computer unistail the rest this should cure your problem

---

### Post by irv on 2011-11-03
> **0121computers said:**
> If your running two internet seach engines at te same time they might be clashing for instance firefox and google chrome clash and so do internet explorer and firefox on some websites so if this is your problem stick to ether internet explorer which usaly works on nearly every site or google chrome is excelent if you are good on your computer unistail the rest this should cure your problem

Internet Explorer in Linux? I don't know many people doing this unless there are running it under Wine.

---

### Post by maxmiaggi on 2012-01-07
Sorry for such late response. I was stuck somewhere..

As required, here are the following details about my system. After a hardware scan, I found the following devices:
Intel Corporation Wireless WiFi Link 5100
Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

Here are a few things I typed in the terminal. It might be useful.

```
mayank@mayank-laptop:~$ sudo lshw -C network
[sudo] password for mayank: 
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:1f:4e:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=172.16.60.59 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:02:14:50
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:fc100000-fc10ffff
```

```
mayank@mayank-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"VOLSBB"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:68:7D:E8:D0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
mayank@mayank-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:02:14:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9968 (9.9 KB)  TX bytes:9968 (9.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:1f:4e:42  
          inet addr:172.16.60.59  Bcast:172.16.60.59  Mask:255.255.255.255
          inet6 addr: fe80::224:d6ff:fe1f:4e42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:676584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92061899 (92.0 MB)  TX bytes:192384 (192.3 KB)
```
```
mayank@mayank-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

---

### Post by maxmiaggi on 2012-01-08
So I searched the internet and found this thread.
[http://ubuntuforums.org/showthread.php?t=1795503](http://ubuntuforums.org/showthread.php?t=1795503)

Here, in the last reply, it says to upgrade the kernel. So I downloaded the latest kernel 3.1.8 from kernel.org. I followed this site for installing the new kernel. 
[http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/](http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/)

But when I write the following in the terminal,
```

make menuconfig

```
it shows up the following error

```

mayank@mayank-laptop:~/Desktop/linux/linux-3.1.8$ make menuconfig
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[1]: *** [scripts/kconfig/dochecklxdialog] Error 1
make: *** [menuconfig] Error 2
```

So, how do I install ncurses without the internet (no wifi, no internet :( )

---

