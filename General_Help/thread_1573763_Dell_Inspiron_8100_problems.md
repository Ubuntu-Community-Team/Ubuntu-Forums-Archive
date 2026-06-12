---
title: "Dell Inspiron 8100 problems"
date: 2010-09-13
forum: General Help
---

### Post by anees27 on 2010-09-13
Hi there,
 
I have a Dell Inspiron 8100 laptop. Installed Lucid Lynx, didn't like it, then put back Windows XP. Now my onboard ethernet port doesn't work.
 
I've re-flashed the BIOS with the original file from Dell, however, it still doesn't work.
 
The weird thing is, that the ethernet port does work under Lucid Lynx.
 
I'm thinking that somehow Lynx modified the NVRAM ?
 
Any ideas ?
 
Thanks,
Anees

---

### Post by viralmeme on 2010-09-13
> **anees27 said:**
> I have a Dell Inspiron 8100 laptop. Installed Lucid Lynx, didn't like it, then put back Windows XP. Now my onboard ethernet port doesn't work.

Post the output of `ifconfig' and  `lshw -C network' ..

---

### Post by anees27 on 2010-09-13
> **viralmeme said:**
> Post the output of `ifconfig' and `lshw -C network' ..
 
I put XP back on. So I can't do the ifconfig.
 
I do know the network port does work under Ubuntu, as I was connected to my router, and was able to surf the web, etc..
 
It is an Intel ether 8255x adaptor.

---

### Post by viralmeme on 2010-09-13
> **anees27 said:**
> I put XP back on. So I can't do the ifconfig.
Boot from the Ubuntu Live CD and post the results ..

---

### Post by anees27 on 2010-09-13
> **viralmeme said:**
> Boot from the Ubuntu Live CD and post the results ..
 
will do tonight and post results tommorrow, thanks!

---

### Post by anees27 on 2010-09-13
> **viralmeme said:**
> Boot from the Ubuntu Live CD and post the results ..

Ok, here goes:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:7b:fa:19  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe7b:fa19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8987 (8.9 KB)  TX bytes:7616 (7.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-7B-FA-19-37-62-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:7b:fa:19  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe7b:fa19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8987 (8.9 KB)  TX bytes:7616 (7.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-7B-FA-19-37-62-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=56 mingnt=8
       resources: memory:f8fff000-f8ffffff ioport:ecc0(size=64) memory:f8e00000-f8efffff
  *-network
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:09:00.0
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:7b:fa:19  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe7b:fa19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8987 (8.9 KB)  TX bytes:7616 (7.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-7B-FA-19-37-62-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=56 mingnt=8
       resources: memory:f8fff000-f8ffffff ioport:ecc0(size=64) memory:f8e00000-f8efffff
  *-network
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:3f:7b:fa:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:28000000-28007fff
ubuntu@ubuntu:~$ 



I'm currently connected on the wireless, as you can see from above.

---

