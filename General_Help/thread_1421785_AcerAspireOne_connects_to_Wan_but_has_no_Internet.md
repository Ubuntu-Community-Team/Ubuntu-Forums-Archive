---
title: "AcerAspireOne connects to Wan but has no Internet"
date: 2010-03-04
forum: General Help
---

### Post by kingarthurpt on 2010-03-04
Hi there. I'm sorry if i'm posting this on the wrong place and if this problem is solved in another post but I couldn't find anything to solve my problem.
I'm kind of noob when it comes to these kinds of problems.

I have an Acer Aspire One 110L. I had Ubuntu 9.04 on it working fine but one day something happened. I connected to my wireless network and I got no Internet. I couldn't even ping to my router. 
I thought it was some kind of bad update I've installed that made it to my computer, so today I've installed Ubuntu 8.10, following this tutorial: [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)
While following it, I used a wireless usb card to connect to my wireless network and download the packages needed. 
I've installed WLan via ath5k Method at the beginning, but right after unpluging the USB wireless card, the other wireless card from my Aspire One had the same problem as before. It can connect to the network but I can't even ping my router. No signal...
I've tried the madwifi method too but the problem is still here, because it must be something else. The drivers must be fine.

Can anyone please tell me what to do here? I'm pissed off already with this problem. I don't really know what is the problem. I have another 2 computers at home and they work fine via Wireless.

Thanks in advance.

---

### Post by grandmaster on 2010-03-04
do you have a wireless switch on the computer anywhere?

GM

---

### Post by kingarthurpt on 2010-03-04
Yes, and it works fine. The LED also works. If I turn the switch off I can't connect to the wireless network anymore. When I turn it on, it connects right away.

aditional info:
- I'm connecting using DHCP, but if I try to choose another IP manually it has the same problem.

- /sbin/route 
```

   Destination   Gateway    Genmask     Flags Metric Ref Use Iface
   192.168.2.0      *     255.255.255.0  U     2     0   0   ath0
   link-local       *     255.255.0.0    U    1000   0   0   ath0
   default   192.168.2.1    0.0.0.0      UG    0     0   0   ath0

```
The default gateway only shows up after 15 seconds. Shouldn't that default gateway's genmask be 255.255.255.0 ? I don't know what are the first 2 routes.

---

### Post by kingarthurpt on 2010-03-04
lshw -C network
```
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b5:9c:6c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:22:69:19:1c:b7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.2.100 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:ee:e1:cb:35:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:22:69:19:1c:b7  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23636 (23.6 KB)  TX bytes:28549 (28.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:b5:9c:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4092 (4.0 KB)  TX bytes:4092 (4.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-22-69-19-1C-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39565 errors:0 dropped:0 overruns:0 frame:3761
          TX packets:1605 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:5467953 (5.4 MB)  TX bytes:129875 (129.8 KB)
          Interrupt:18 

```

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
```

iwlist scan
```
ath0      Scan completed :
          Cell 01 - Address: 00:22:2D:04:19:5A
                    ESSID:"kingarthurpt"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-55 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:17:4B:22:8E
                    ESSID:"ThomsonBF765F"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101880003a4000027a4000042435e0062322f00
          Cell 03 - Address: 00:1D:5A:46:C1:C9
                    ESSID:"2WIRE-PT-497"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s
                    Extra:bcn_int=100

```

can anyone help please?

---

### Post by kingarthurpt on 2010-03-05
anyone?

---

### Post by haydoni on 2010-03-05
That's very strange. I have the same model and have had no such problems, it all works out of the box.

You might get better luck posting [here - aspire one users forum.]("http://www.aspireoneuser.com/forum/viewforum.php?f=28")

---

### Post by ibuclaw on 2010-03-05
What driver is being used to control the wifi card?
Can you post the output of:
```
lsmod | grep acer_wmi
```
and
```
lsmod | grep ath
```
and
```
grep -nR "ath" /etc/modprobe.d
```

Regards
Iain

---

### Post by CongoJim on 2010-03-05
I had the same problem. When I checked my settings under "wireless" "IPv6" and changed it to "ignore" problem went away. Coulda been a coincidence as well and the reboot fixed it.

---

### Post by kingarthurpt on 2010-03-05
lsmod | grep acer_wmi
```
(nothing)
```

lsmod | grep ath
```
ath_rate_sample        20736  1 
ath_pci               222008  0 
wlan                  240112  6 wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312288  3 ath_rate_sample,ath_pci

```

grep -nR "ath" /etc/modprobe.d
```
/etc/modprobe.d/blacklist-local:1:blacklist ath5k
/etc/modprobe.d/blacklist-local:2:blacklist ath_pci
/etc/modprobe.d/blacklist-wifi.conf:2:# blacklist ath5k

```

hmmm.. is this meaning that my driver is blacklisted? Since I'm using ath_pci now.. Should I remove these lines from that file?


about ignoring IPv6, actually I've done something in the alias to disable it yesterday, but I can't remember if it was before or after formating it and installing Ubuntu 8.10 again.

I've seen more people complaining about this problem but I can't find a solution for my own. 

I'm going to try to "remove" those lines from /etc/modprobe.d and if it doesn't help, I'm thinking about installing the new 9.10 netbook remix. I read the wireless works out of the box... like it was supposed to work with 8.10

---

### Post by ibuclaw on 2010-03-05
> **kingarthurpt said:**
> lsmod | grep acer_wmi
```
(nothing)
```

lsmod | grep ath
```
ath_rate_sample        20736  1 
ath_pci               222008  0 
wlan                  240112  6 wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312288  3 ath_rate_sample,ath_pci

```

grep -nR "ath" /etc/modprobe.d
```
/etc/modprobe.d/blacklist-local:1:blacklist ath5k
/etc/modprobe.d/blacklist-local:2:blacklist ath_pci
/etc/modprobe.d/blacklist-wifi.conf:2:# blacklist ath5k

```

hmmm.. is this meaning that my driver is blacklisted? Since I'm using ath_pci now.. Should I remove these lines from that file?


about ignoring IPv6, actually I've done something in the alias to disable it yesterday, but I can't remember if it was before or after formating it and installing Ubuntu 8.10 again.

I've seen more people complaining about this problem but I can't find a solution for my own. 

I'm going to try to "remove" those lines from /etc/modprobe.d and if it doesn't help, I'm thinking about installing the new 9.10 netbook remix. I read the wireless works out of the box... like it was supposed to work with 8.10

The problem is that you should be using the **ath5k** driver, and not the ath_pci.

When you run:
```
cat /etc/modprobe.d/blacklist-local
```
Does it just output:
```

blacklist ath5k
blacklist ath_pci

```
If so, should be OK to delete it.
```
sudo rm /etc/modprobe.d/blacklist-local
```
If not, then just remove the those two lines from the file then (as they are undesirable / unneeded there).


Then edit the blacklist wifi list.
```
sudo gedit /etc/modprobe/blacklist-wifi.conf
```
And at the bottom, add:
```

blacklist ath_pci
blacklist ath_hal

```
Then reboot.

Regards
Iain

---

### Post by kingarthurpt on 2010-03-05
I'm really pissed off because I treat this computer with care all the time and now it's broken or it looks like it.
I did it, ibuclaw, but now I can't scan any network.
When using lshw -C network, I can see that the driver is ath5k, but when using iwlist scan, I got "No scan results" for wlan1 interface.

before your post I downloaded Ubuntu 9.10 Netbook Remix and put it on a USB drive, booted the Aspire One through the USB and when using 9.10, I easily connected to the network but still got the original problem. Don't have internet, can't ping router...

---

