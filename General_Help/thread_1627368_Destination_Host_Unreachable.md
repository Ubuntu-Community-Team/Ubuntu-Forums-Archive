---
title: "Destination Host Unreachable"
date: 2010-11-21
forum: General Help
---

### Post by dinesh.sarsar on 2010-11-21
hi,
   i am new user for ubuntu 10.10, i have a dual operating system windows xp and ubuntu 10.10, i am unable to connect to internet form ubuntu while windows work perfectly, i have a wired connection of sify broadband, when i ping my default gate way i get the following message 

 sahil@ubuntu:~$ ping 10.30.48.1
    PING 10.30.48.1 (10.30.48.1) 56(84) bytes of data.
    From 10.30.48.44 icmp_seq=22 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=23 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=24 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=27 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=37 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=38 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=39 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=42 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=44 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=45 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=46 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=47 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=48 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=49 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=52 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=98 Destination Host Unreachable
    From 10.30.48.44 icmp_seq=99 Destination Host Unreachable
    [FONT=&quot]From 10.30.48.44 icmp_seq=100 Destination Host Unreachable[/FONT]

---

### Post by spikoley on 2010-11-21
Post the results from the following commands.

```
ifconfig -a
```

```
sudo dhclient
```

---

### Post by dinesh.sarsar on 2010-11-22
sahil@ubuntu:~$ ifconfig –a
    –a: error fetching interface information: Device not found
    sahil@ubuntu:~$ sudo dhclient
    [sudo] password for sahil: 
    Internet Systems Consortium DHCP Client V3.1.3
    Copyright 2004-2009 Internet Systems Consortium.
    All rights reserved.
    For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
     
   
  Listening on LPF/eth0/00:16:ec:8c:be:60
    Sending on   LPF/eth0/00:16:ec:8c:be:60
    Sending on   Socket/fallback
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
    DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
    [FONT=&quot]No DHCPOFFERS received.[/FONT]

---

### Post by spikoley on 2010-11-22
> **dinesh.sarsar said:**
> sahil@ubuntu:~$ ifconfig –a
    –a: error fetching interface information: Device not found
    sahil@ubuntu:~$ sudo dhclient
    [sudo] password for sahil: 
    Internet Systems Consortium DHCP Client V3.1.3
    Copyright 2004-2009 Internet Systems Consortium.
    All rights reserved.
    For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


That is weird, it didn't bring up any interfaces.  What are the results when you run *ifconfig* by itself?

Post the results of this command.

```
lspci
```

---

### Post by dinesh.sarsar on 2010-11-23
sahil@ubuntu:~$ ifconfig
    eth0      Link encap:Ethernet  HWaddr 00:16:ec:8c:be:60  
              inet addr:10.30.48.44  Bcast:10.30.48.255  Mask:255.255.255.0
              inet6 addr: fe80::216:ecff:fe8c:be60/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:98904 errors:27544 dropped:0 overruns:0 frame:0
              TX packets:1410 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:7331017 (7.3 MB)  TX bytes:102353 (102.3 KB)
              Interrupt:20 Base address:0xe400 
     
   
  lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:21 errors:0 dropped:0 overruns:0 frame:0
              TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:1872 (1.8 KB)  TX bytes:1872 (1.8 KB)
     
   
  sahil@ubuntu:~$ lspci
    00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
    00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
    00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
    00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
    00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
    00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
    00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
    00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
    00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
    00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
    00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
    01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
    02:03.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem
    02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    [FONT=&quot]02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)[/FONT]

---

### Post by iiiears on 2010-11-23
The hardware looks ok to a naive eye like mine. lsmod to double check and then gksudo /etc/hosts for a correct local hostname in this case "127.0.0.1 ubuntu" maybe?

cheers.

---

### Post by dcstar on 2010-11-23
> **dinesh.sarsar said:**
> hi,
   i am new user for ubuntu 10.10, i have a dual operating system windows xp and ubuntu 10.10, i am unable to connect to internet form ubuntu while windows work perfectly, **i have a wired connection of sify broadband**,
.........

And **exactly** how is Windows set up to use this?

---

### Post by dinesh.sarsar on 2010-11-23
Please find the file attached for windows internet configuration in working state.

---

### Post by dinesh.sarsar on 2010-11-23
[]("i:%5CUbuntuforums%5CWindows%20Screen%20Shot.JPG")sorry missed the attachment earlier, please find it attached now.

---

### Post by spikoley on 2010-11-24
I think it has to do with your Sify broadband log in.  What type of internet connection do you have?  It looks like others have had issues with Sify.  Check some of [their threads]("http://ubuntuforums.org/search.php?searchid=77638995").  

I think [this post]("http://ubuntuforums.org/showpost.php?p=8221463&postcount=2") might fix it.

> Type the following in the terminal.

$ sudo pppoeconf

Choose default options for everything. Enter your internet username and password when asked. You should be able to connect, if everything goes all right.

---

