---
title: "Some Help needed :)"
date: 2009-12-31
forum: General Help
---

### Post by zonefull on 2009-12-31
hello guys im new here in using dis great operating system i dled ubuntu 9.10 and i got it ready on ma pc but after the setup process is done i couldnot get it attached to my LAN or internet connection i use a DHCP router wich need no configuration as it was shown problem is even my acctivity lamp on da router doesnot give any activity light not even a blink wish u guys can help me out thx for reading an cya :)

---

### Post by Iowan on 2009-12-31
Wow - not a single period in the entire post... :)
Post results of **sudo lshw -C network** and **ifconfig -a**.

---

### Post by zonefull on 2009-12-31
thx for answering :P i got what u asked for :D
sudo lshw -Cnetwork
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
    
   lshw -version

    -version        print program version (B.02.14)

format can be
    -html      
     output hardware tree as HTML
    -xml            output hardware tree as XML
    -short       
   output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    
only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS     
   same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST  
  enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize     
  sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric       
 output numeric IDs (for PCI, USB, etc.)













ifconfig -a
eth0    
  Link encap:Ethernet  
HWaddr 00:16:e6:3c:76:9b  
         
 UP BROADCAST MULTICAST  MTU:1500  Metric:1
       
   RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       
  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         
 collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo      
  Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
         
 inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wish it was that i guess i need to hmm somethin like enabling connection in windows or so
cuz no activity from the cable detected on the router

---

### Post by Iowan on 2010-01-01
> **zonefull said:**
> 
sudo lshw -Cnetwork Spacing is important - try it as ```
sudo lshw -C network
```It appears that the interface has no IP address - next step will be to try to determine why...

---

### Post by zonefull on 2010-01-01
i got it  sorry its missd up as i copy from Ubuntu :D

sudo lshw -C network


*-network      
         
       description: Ethernet interface
  
     product: 82801EB/ER (ICH5/ICH5R) integrated LAN Controller
   
    vendor: Intel Corporation
       physical id: 8
       
bus info: pci@0000:01:08.0
       logical name: eth0
    
  version: 02
       serial: 00:16:e6:3c:76:9b
       size: 10MB/s
  
     capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A 
latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
      
 resources: irq:20 memory:f8000000-f8000fff ioport:a000(size=64)


Also ifconfig
eth0    
  Link encap:Ethernet 
 HWaddr 00:16:e6:3c:76:9b  
       
   UP BROADCAST MULTICAST  MTU:1500  Metric:1
     
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         
 collisions:0 txqueuelen:1000 
         
 RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



eth0:avahi Link encap:Ethernet 
HWaddr 00:16:e6:3c:76:9b  
          inet addr:169.254.8.118  Bcast:169.254.255.255 
Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        

Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
   
inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
         
 TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
         
 collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wish thats it :) thx for ur help

---

### Post by zonefull on 2010-01-01
none get a clue >.<

---

### Post by Iowan on 2010-01-01
Well, interface isn't disabled. The **avahi** address means it didn't get address from DHCP server.  Have you verified that the cable is good and the router port is working?

---

### Post by zonefull on 2010-01-01
yea i did cuz its aready working good on windows im using the same pc now >.< u think theres no solution :( but when Ubuntu boots up the activity lamb on the router meaning the cable in conected gets of i dk why either

---

### Post by zonefull on 2010-01-01
:(

---

### Post by Hwæt on 2010-01-01
What company made the router? And if possible, could you please tell me the model number? It's normally written on the bottom, top, or side of the router.

---

### Post by zonefull on 2010-01-02
its TP-Link and model TD-8840 kinda old i guess

---

### Post by HappyFeet on 2010-01-02
Try going directly from the modem to your computer. That way we will know if it is the router at fault.

---

### Post by zonefull on 2010-01-02
i dk how to do that sorry but router is aready working on windows now im using it this moment :(

---

### Post by zonefull on 2010-01-02
how do i enable firmware i got intell pro/100 network adabter

---

