---
title: "wireless connect not working in 9.10"
date: 2009-12-23
forum: General Help
---

### Post by gretarsson on 2009-12-23
I can use wire connect but not wireless my laptop can not find my rouder how do I set it up manual? I have put up ssid name and try to put in ip address mask, gate and DNS address but still nothing

decima@decima-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by theDaveTheRave on 2009-12-23
gretarrson,

can you send the output of the following.

```

iwlist scan

```

will show the avialable wifi networks, just to confirm that you are seeing them, and on what interface.

it may also give you a clue as to why you can't connect, you may then need to bring up the appropriate interface.

Also the output of
```

ifconfig

```

will show up the 2 interfaces that work together. For instance if you have wmaster0 and wlan0 they should have related hardware addresses (as one is a 'pseudo' device).

the combination of your previous output and the above should throw some light on the problem.

David

---

### Post by gretarsson on 2009-12-23
> **theDaveTheRave said:**
> gretarrson,

can you send the output of the following.

```

iwlist scan

```

will show the avialable wifi networks, just to confirm that you are seeing them, and on what interface.

it may also give you a clue as to why you can't connect, you may then need to bring up the appropriate interface.

Also the output of 
```

ifconfig

```

will show up the 2 interfaces that work together. For instance if you have wmaster0 and wlan0 they should have related hardware addresses (as one is a 'pseudo' device).

the combination of your previous output and the above should throw some light on the problem.

David

Here is my outprint from terminal

decima@decima-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

decima@decima-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:f5:17:e5  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fef5:17e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97623 (97.6 KB)  TX bytes:25315 (25.3 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

decima@decima-laptop:~$

---

### Post by theDaveTheRave on 2009-12-23
> **gretarsson said:**
> Here is my outprint from terminal

decima@decima-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down



that may have something to do with it, 'Network is down' ! confirm that your wireless router has it's wifi turned on, normally you'll pick up all the local wifi networks with that, and I'm surprised that there are no others near you!

However your ifconfig doesn't have any details for you wmaster0 interface.

can you post the output of the following

```

lshw -C network

```

that will confirm that you network card is working OK. I've posted mine below as an example.

> 
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.135 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 02:64:25:13:c5:21
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



David

---

### Post by gretarsson on 2009-12-23
> **theDaveTheRave said:**
> that may have something to do with it, 'Network is down' ! confirm that your wireless router has it's wifi turned on, normally you'll pick up all the local wifi networks with that, and I'm surprised that there are no others near you!

However your ifconfig doesn't have any details for you wmaster0 interface.

can you post the output of the following

```

lshw -C network

```

that will confirm that you network card is working OK. I've posted mine below as an example.



David

Hi again and thanks for your time my wireless is up in my rouder and same in my laptop and I had window 7 before and it was working fine but after I install ubuntu 9.10 it did not work and my wife is not so happy about that (it is her pc) but her is out print from terminal

ecima@decima-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:f5:17:e5
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5788-v3.26 ip=192.168.1.36 latency=64 mingnt=64 multicast=yes
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0010000-d0011fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:6c:ee:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
decima@decima-laptop:~$

---

### Post by theDaveTheRave on 2009-12-28
hello again.

sorry for the slow reply, too much food being eaten and no internet for 4 days (must be a record for me!)

Well I hope you had a good christmas, and we can now try to continue from where we left off last week.

It seems as though your card is being recognised etc so try the following.

```

sudo ifconfig wlan0 up

```

then try the the

```

iwlist scan

```
again to see if there is any change in the output.

Also from the output you posted it would seem that you are using a broadcom chipset for both ethernet and wifi, specifically for your wifi you are using the BCM4318 chipset.

I would recomend doing a quick search for it on the forum, I may be able to help but have no personal experience of this chip, so the help will only be coming second hand from another thread on the forum.

sorry I'm not going to be much more help on this one....

David

---

### Post by bkratz on 2009-12-28
Found this on the networking and wireless forum (didn't look at it though!)

[http://ubuntuforums.org/showthread.php?t=1366540](http://ubuntuforums.org/showthread.php?t=1366540)

---

### Post by Jose Catre-Vandis on 2009-12-28
Um, unplug your wired connection before trying to connect wirelessly (sounds obvious, but can cause problems!)

---

### Post by gretarsson on 2009-12-30
> **theDaveTheRave said:**
> hello again.

sorry for the slow reply, too much food being eaten and no internet for 4 days (must be a record for me!)

Well I hope you had a good christmas, and we can now try to continue from where we left off last week.

It seems as though your card is being recognised etc so try the following.

```

sudo ifconfig wlan0 up

```

then try the the

```

iwlist scan

```
again to see if there is any change in the output.

Also from the output you posted it would seem that you are using a broadcom chipset for both ethernet and wifi, specifically for your wifi you are using the BCM4318 chipset.

I would recomend doing a quick search for it on the forum, I may be able to help but have no personal experience of this chip, so the help will only be coming second hand from another thread on the forum.

sorry I'm not going to be much more help on this one....

David

Hi again and Merry Christmas, hope you had good time, dont take all your time in helping me, all I can find in google isbroadcom card is not good for linux but my wlan0 can not find my card other computer (windows) can find my wirelwss rouder so I know my problem is in my laptop. Thanks again for your time here is my outprint

decima@decima-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
decima@decima-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.

decima@decima-laptop:~$ 

decima@decima-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

decima@decima-laptop:~$ lspci | grep Broadcom\ Corporation
02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
decima@decima-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by gretarsson on 2009-12-30
> **Jose Catre-Vandis said:**
> Um, unplug your wired connection before trying to connect wirelessly (sounds obvious, but can cause problems!)

Hi and happy holly days, it is true wlan0 show different out print if lan cable is unplug but still same

decima@decima-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

decima@decima-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
decima@decima-laptop:~$

---

### Post by ssmanian on 2009-12-30
I am having the exact same issue with ubuntu 9.10 with my Dell Inspiron running broadcom chipset BCM4311. The wired connection works just fine. I went through the instructions in
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

that didnt help either. 

Some outputs from questions in this thread, Any help is greatly appreciated.

senthiladmin@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

senthiladmin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:61:ee:1d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

senthiladmin@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:61:ee:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:4d:aa:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
senthiladmin@ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for sadmin: 
SIOCSIFFLAGS: No such file or directory

---

### Post by bkratz on 2009-12-30
> **ssmanian said:**
> I am having the exact same issue with ubuntu 9.10 with my Dell Inspiron running broadcom chipset BCM4311. The wired connection works just fine. I went through the instructions in
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

that didnt help either. 

Some outputs from questions in this thread, Any help is greatly appreciated.

senthiladmin@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

senthiladmin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:61:ee:1d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

senthiladmin@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:61:ee:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:4d:aa:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
senthiladmin@ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for sadmin: 
SIOCSIFFLAGS: No such file or directory




You really should be ok with running the sta driver rather than the b43 see this thread

[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom)

---

### Post by ssmanian on 2009-12-30
I was able to get my wireless working by following this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Still I cannot connect consistently with my WEP Secured access-point but I can connect to the unsecured network and connect to the internet. That is a big step forward.

Thanks for the help.

Senthil

---

### Post by theDaveTheRave on 2010-01-05
Hello again...

I hope everyone has had a good christmass / new years.

I'm looking through the various posts in this thread, and I wondering what modules you need to have installed for your broadcom wireless chips to work?

```

lsmod

```

will tell you what is instaled on your system, you would then need to confirm this with the users in other threads that have been linked to here. There may also be a requirement to "blacklist" some modules to prevent interference.

If you don't have the required modules, then the communications isn't going to work however hard you try :(

Sorry this post may not be that much help, but it is currently the best I can offer, especially as I don't have a broadcom chip floating around.

The other options are to check out things like NDISwrapper, they may have a method to get the card working by "translating" the module normaly used in the windows environment, again it may well be you need to "blacklist" some modules, as NDISwrapper was more common on older kernels.

David

---

