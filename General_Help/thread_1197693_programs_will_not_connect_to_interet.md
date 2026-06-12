---
title: "programs will not connect to interet"
date: 2009-06-26
forum: General Help
---

### Post by poliltimmy on 2009-06-26
Hey Guys,

 My power supply blew up. I replaced it but for some reason my Pidgin and Tranny will not connect to the net. They load up but no connection. No problem with my browsers. Could the two problems be related. All was fine before the power supply went out. I am running Jaunty now. I guess while I flipping back and forth I duplicated this post, sorry.

T-bird connects as well. seems all external apps connect interal apps do not.

---

### Post by Greyfox_75 on 2009-06-26
First try running this

dhclient

Try your inernet and see if it works.  If not try opening a terminal and run these

ping google.com
ifconfig
lspci

post your output. (I suppose you don't have internet to post them hmm.)
Assuming you have a jumpdrive or some other way to transfer files do this instead.

ping google.com > ping.txt
ifconfig > ifconfig.txt
lspci > lspci.txt

and put those 3 txt files on a jump drive or some other way that will let you transfer files and post them here.

---

### Post by poliltimmy on 2009-06-26
~$ ping google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=52 time=58.3 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=52 time=58.2 ms

timmy@timmy-pawpawsliltoy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8f:b0:73:c9  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:feb0:73c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82744387 (82.7 MB)  TX bytes:19243171 (19.2 MB)
          Interrupt:36 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4463 (4.4 KB)  TX bytes:4463 (4.4 KB)

timmy@timmy-pawpawsliltoy:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T890CF Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. VT3351 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

I got tranny running by doing a purge and reinstall, Pidgin is still a no go. Thanks for you help in advance!!!

---

### Post by Greyfox_75 on 2009-06-26
SInce your ping is working it seems like it has nothing to do with your internet.  

Are you trying to connect to yahoo? As of friday yahoo changed a few things on their servers that locked out "old" clients.

Try this.
[http://kenno.wordpress.com/2009/06/20/pidgin-2-5-5-cannot-connect-to-yahoo-messenger/](http://kenno.wordpress.com/2009/06/20/pidgin-2-5-5-cannot-connect-to-yahoo-messenger/)

---

### Post by poliltimmy on 2009-06-26
Thanks man!!! My computer was down since the 2nd. Glad nothing major happened. All is fine now Thanks a bunch!:popcorn:

---

