---
title: "Internet not working"
date: 2011-10-01
forum: General Help
---

### Post by Maizy on 2011-10-01
Hi,

I bought a new laptop yesterday and put linux on it today, replacing Windows 7 (but i made recovery disks so i hope i can get it back if i need to...). The problem I've got is that the internet isn't working.

I plug the ethernet cable straight from my router into my laptop. A message pops up saying "Auto Eth0: connected", but nothing actually works (ie pages loading on firefox), and shortly it changes to "disconnected". Of it's own accord it turns back on and off periodically. The internet is working fine throughout the rest of the house.

I have no idea where to start fixing this so any help is, of course appreciated :) it might be a simple tick-box or i might need a new driver...

Thanks!

---

### Post by papibe on 2011-10-01
Welcome to the forums!

Could you post the result of these commands?
```
$ sudo lshw -C network

$ lspci -nn | grep -i eth

$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com

```
Please use the # tags (CODE tags) to paste your results.
Regards.

---

### Post by Maizy on 2011-10-01
Embarrasing newbie question... how do you use the code tags? (I tried plain hashes and <>)

```


[sudo] password for maizy: 
      *-network UNCLAIMED     
           description: Network controller
           product: Broadcom Corporation
           vendor: Broadcom Corporation
           physical id: 0
           bus info: pci@0000:02:00.0
           version: 01
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list
           configuration: latency=0
           resources: memory:90100000-90103fff
      *-network
           description: Ethernet interface
           product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: eth0
           version: 02
           serial: 78:ac:c0:4e:fb:12
           size: 100MB/s
           capacity: 100MB/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.115 latency=0 link=yes multicast=yes port=MII speed=100MB/s
           resources: irq:26 ioport:2000(size=256) memory:90010000-90010fff(prefetchable) memory:90000000-9000ffff(prefetchable) memory:90020000-9002ffff(prefetchable)
    maizy@Maizys-laptop:~$ lspci -nn | grep -i eth
    03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    maizy@Maizys-laptop:~$ ifconfig
    eth0      Link encap:Ethernet  HWaddr 78:ac:c0:4e:fb:12  
              inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
              inet6 addr: fe80::7aac:c0ff:fe4e:fb12/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:128 errors:0 dropped:0 overruns:0 frame:0
              TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:25739 (25.7 KB)  TX bytes:37779 (37.7 KB)
              Interrupt:26 Base address:0x4000 
     
   
  lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:981 errors:0 dropped:0 overruns:0 frame:0
              TX packets:981 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:87532 (87.5 KB)  TX bytes:87532 (87.5 KB)
     
   
  maizy@Maizys-laptop:~$ route -n
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
    169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
    0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
    maizy@Maizys-laptop:~$ nslookup ubuntu.com
    ;; connection timed out; no servers could be reached
     
   
  maizy@Maizys-laptop:~$ dig ubuntu.com
     
   
  ; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
    ;; global options: +cmd
    ;; connection timed out; no servers could be reached
    maizy@Maizys-laptop:~$ 
    
```

Here you go!

---

### Post by gandaran on 2011-10-01
> **Maizy said:**
> Hi,

I bought a new laptop yesterday and put linux on it today, replacing Windows 7 (but i made recovery disks so i hope i can get it back if i need to...). The problem I've got is that the internet isn't working.

I plug the ethernet cable straight from my router into my laptop. A message pops up saying "Auto Eth0: connected", but nothing actually works (ie pages loading on firefox), and shortly it changes to "disconnected". Of it's own accord it turns back on and off periodically. The internet is working fine throughout the rest of the house.

I have no idea where to start fixing this so any help is, of course appreciated :) it might be a simple tick-box or i might need a new driver...

Thanks!
check the router setup if DCHP server is enabled

---

### Post by Maizy on 2011-10-01
It is enabled, yes.

It's probably worth mentioning that there's a desktop computer running ubuntu on the network and that a laptop I plugged in a few days ago with ubuntu on worked fine (same cable), so the problem is likely with my laptop.

---

### Post by gandaran on 2011-10-01
> 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
try disabling network on the network manager panel icon and go to edit connections and remove from the wired tab any existing connection setups then wait two or three minutes to enable the network again, should fix the problem.

---

### Post by Maizy on 2011-10-01
tried that, didn't work, same problem =(

thanks anyway though

---

### Post by papibe on 2011-10-01
Let's see if you can reach your router:
```
$ ping -c 3 192.168.1.1
```
And then a server on the Internet (ubuntu.com):
```
$ ping -c 3 91.189.94.156
```
Could you post the results of those commands?

BTW, to use code tags, press the # symbol on the tools while editing your post. Then paste the result between the tags.

Regards.

---

### Post by Maizy on 2011-10-01
```
  maizy@Maizys-laptop:~$ ping -c 3 192.168.1.254
    PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
    From 192.168.1.115 icmp_seq=1 Destination Host Unreachable
    From 192.168.1.115 icmp_seq=2 Destination Host Unreachable
    From 192.168.1.115 icmp_seq=3 Destination Host Unreachable
     
   
  --- 192.168.1.254 ping statistics ---
    3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
    , pipe 3
    
```


I didn't ping the server as I figure if I can't get to my router then the server is off limits too...

---

### Post by papibe on 2011-10-01
Oops I'm sorry, that was the LAN address of my own router, it should be 192.168.1.1

(I fixed it above)

---

### Post by Maizy on 2011-10-01
That got rid of the three errors but still no success:

```
  maizy@Maizys-laptop:~$ ping -c 3 192.168.1.1
    PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
     
   
  --- 192.168.1.1 ping statistics ---
    3 packets transmitted, 0 received, 100% packet loss, time 2015ms
    
```

---

### Post by papibe on 2011-10-01
Does this give you any error?
```
$ sudo service network-manager restart
```
What happens when you ping again after that?

Regards.

---

### Post by Maizy on 2011-10-01
I did it twice as I didn't wait long enough first time

```

  maizy@Maizys-laptop:~$ sudo service network-manager restart
    [sudo] password for maizy: 
    network-manager start/running, process 4013
    maizy@Maizys-laptop:~$ ping -c 3 192.168.1.1
    connect: Network is unreachable
    maizy@Maizys-laptop:~$ ping -c 3 192.168.1.1
    PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
    From 192.168.1.115 icmp_seq=2 Destination Host Unreachable
    From 192.168.1.115 icmp_seq=3 Destination Host Unreachable
     
   
  --- 192.168.1.1 ping statistics ---
    3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2015ms
    , pipe 2
    maizy@Maizys-laptop:~$ sudo service network-manager restart
    network-manager start/running, process 4071
    maizy@Maizys-laptop:~$ ping -c 3 192.168.1.1
    PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
    From 192.168.1.115 icmp_seq=2 Destination Host Unreachable
    From 192.168.1.115 icmp_seq=3 Destination Host Unreachable
     
   
  --- 192.168.1.1 ping statistics ---
    3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2015ms
    , pipe 2
    maizy@Maizys-laptop:~$


```

---

### Post by papibe on 2011-10-01
I'm running out of ideas. This has helped some people before:
```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 mtu 1024
$ sudo ifconfig eth0 up
```
Then try both pings again.

Regards.

---

### Post by Maizy on 2011-10-01
Didn't change it, exactly the same result on pinging the router (100% packet loss +2 errors) =(

---

### Post by drdos2006 on 2011-10-01
Well, he is getting an Internet address... inet addr:192.168.1.115

So it might be a browser issue.
If Firefox, type "about:config" in the toolbar.
Filter on "IPv6", click and toggle "network.dns.diasbleIPv6" to True.

Might help.

regards

---

### Post by Maizy on 2011-10-02
Good news! I turned it on this morning and it worked. So maybe I should've tried just restarting it (no idea why it happened though)... Sorry for wasting your time and thanks for the help :)

---

