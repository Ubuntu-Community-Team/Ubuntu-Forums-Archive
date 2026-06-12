---
title: "Lost my network manager"
date: 2010-03-01
forum: General Help
---

### Post by ibrahim.k on 2010-03-01
Hi,

I was trying to install gnome network manager (they told it is better for ICS)

After installing it I have deleted my network manager and now I can't find anyone of them!!!  

No wireless connection for the internet nothing at all .

what should I do to get the network manager back ?

---

### Post by hwttdz on 2010-03-01
To get network manager back try "sudo apt-get install network-manager-gnome" after booting with a wired connection.  You might have to re-add notification applet to the panel.

---

### Post by ibrahim.k on 2010-03-02
[hwttdz]("http://ubuntuforums.org/member.php?u=175488") I can't get an internet connection at all I have tryied to but no way !! is there anway that i can install it via a deb package or something like this ?  thnx

---

### Post by stoneage on 2010-03-02
If you can access the internet somewhere else you can download from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by ibrahim.k on 2010-03-02
Stoneage Thank you for telling me that I didn't think about it :$ after installing it successfully and restarting the laptop i can see its icon on the notification area but the network manager is not detecting any networks !!!! what can I do about this ?

---

### Post by Arijit_Kundu on 2010-03-02
firstly, what kind of network connections do you have? And were they working before?

---

### Post by ibrahim.k on 2010-03-02
I have a wired and wireless they were working perfectly now I can't even find the wireless ! the network manager is not detecting anything

---

### Post by Arijit_Kundu on 2010-03-02
can you post the output by running 'ifconfig' (without quotes) in the terminal?

---

### Post by ibrahim.k on 2010-03-02
This is the output from ifconfig, I am sorry its taking long time from me to respond 

ibrahim@ibrahim-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:6a:8f:d4  
          inet addr:192.168.0.83  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe6a:8fd4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49505 (49.5 KB)  TX bytes:12146 (12.1 KB)
          Interrupt:31 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5331 (5.3 KB)  TX bytes:5331 (5.3 KB)

pan0      Link encap:Ethernet  HWaddr ee:ea:85:1b:89:c5  
          inet6 addr: fe80::ecea:85ff:fe1b:89c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:6836 (6.8 KB)

pan0:avahi Link encap:Ethernet  HWaddr ee:ea:85:1b:89:c5  
          inet addr:169.254.9.67  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:5f:7d:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:21:6b:5f:7d:1e  
          inet addr:169.254.5.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

ibrahim@ibrahim-laptop:~$

---

### Post by Arijit_Kundu on 2010-03-02
I think your eth0 & wlan0 are already connected! It is showing IP addresses. Are there any authentication for the connection? (like username password).

if not, run 'sudo lshw -C network' and post the output here.

---

### Post by ibrahim.k on 2010-03-02
there is password for the wireless connection I have deleted it, I thought this might fix the problem (no notifications for any connection was showing up) my wireless connection name is not wlan0 it is ag-office I will use 'sudo lshw -C network' anyway thnx in advance

---

### Post by Arijit_Kundu on 2010-03-02
wlan0 was not the name.. it is just the port. You can edit the connection passwords by right clicking on the network manager button.

---

### Post by ibrahim.k on 2010-03-02
when i press the left click on the network manager he is telling me that device is not managed for both wired and wireless

ibrahim@ibrahim-laptop:~$ sudo lshw -c network
[sudo] password for ibrahim: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:5f:7d:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:dc000000-dc001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:6a:8f:d4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:5000(size=256) memory:d4010000-d4010fff(prefetchable) memory:d4000000-d400ffff(prefetchable) memory:d4020000-d402ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
ibrahim@ibrahim-laptop:~$

---

### Post by Arijit_Kundu on 2010-03-02
this also seems ok. you can edit network connections from menu (system > preference > network connectons).

Also, try running 

ifconfig eth0 up

and check connection in web browser. 

Also, check /etc/network/interfaces  to verify an entry similar to:

auto eth0
iface eth0 inet dhcp

---

