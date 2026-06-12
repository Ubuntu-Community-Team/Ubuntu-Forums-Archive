---
title: "Has anyone had this problem with 9.10"
date: 2009-11-03
forum: General Help
---

### Post by Rick Abraham on 2009-11-03
Hi guys when I installed Ubuntu 9.04 it automatically detected my wireless adapter and allowed me to access the internet.
I did a fresh install of Ubuntu 9.10 and after the installation it did not detect my wireless card and I cannot find any Linux drivers to download.

I just carnt understand why it worked with 9.04 but wont with 9.10.
Has anyone else had a similar problem.

---

### Post by Peter09 on 2009-11-03
Can you post the output of the terminal commands

```
ifconfig
```
and
```
lshw -C network
```

---

### Post by Rick Abraham on 2009-11-03
Hi Peter09 her are the terminal outputs of the 2 commands you gave me.

  	 	 	 	 	 	  ubuntu@ubuntu-desktop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:13:72:dd:49:e0   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:78 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:78 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:8647 (8.6 KB)  TX bytes:8647 (8.6 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:1b:11:c9:c7:43   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 wlan1     Link encap:Ethernet  HWaddr 00:1c:df:cb:0f:70   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 wmaster0  Link encap:UNSPEC  HWaddr 00-1B-11-C9-C7-43-00-00-00-00-00-00-00-00-00-00   
           UP RUNNING  MTU:0  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 wmaster1  Link encap:UNSPEC  HWaddr 00-1C-DF-CB-0F-70-00-00-00-00-00-00-00-00-00-00   
           UP RUNNING  MTU:0  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 ubuntu@ubuntu-desktop:~$  
 

 

   ubuntu@ubuntu-desktop:~$ lshw -c network  
 WARNING: you should run this program as super-user.  
   *-network:0              
        description: Wireless interface  
        product: RT2561/RT61 rev B 802.11g  
        vendor: RaLink  
        physical id: 3  
        bus info: pci@0000:03:03.0  
        logical name: wmaster0  
        version: 00  
        serial: 00:1b:11:c9:c7:43  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list logical ethernet physical wireless  
        configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11bg  
        resources: irq:19 memory:ebdf8000-ebdfffff  
   *-network:1  
        description: Ethernet interface  
        product: 82801G (ICH7 Family) LAN Controller  
        vendor: Intel Corporation  
        physical id: 8  
        bus info: pci@0000:03:08.0  
        logical name: eth0  
        version: 01  
        serial: 00:13:72:dd:49:e0  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes  
        resources: irq:20 memory:ebdf7000-ebdf7fff ioport:c8c0(size=64)  
   *-network  
        description: Wireless interface  
        physical id: 3  
        logical name: wlan1  
        serial: 00:1c:df:cb:0f:70  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn  
 ubuntu@ubuntu-desktop:~$ 



LOL this all means nothing to me.

---

### Post by Peter09 on 2009-11-03
I think this bug is the problem and if you follow the links through there is a work around.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1820665.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1820665.html)

---

