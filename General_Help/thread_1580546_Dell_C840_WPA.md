---
title: "Dell C840 WPA"
date: 2010-09-23
forum: General Help
---

### Post by xcrogers on 2010-09-23
Hello, 

Cannot connect to my wireless through my card. 

So forgive me for developing a thread for which there are already hundreds. I recently decided to bring my old Dell Latitude C840 laptop back to life with Ubuntu 10.04. I am a total linux beginner but it seemed like a fun exercise. Everything seems to work fine and the system runs great on the computer. I haven't explored too much but I can only connect to the internet directly through an Ethernet connection. The wireless card (Dell truemobile 1150) will find and display available networks but I cannot connect. It simply re-prompts for the password request.

I would appreciate anyone's help in a good thread that I can use to fix this problem (baring in mind that it should be reasonably followable). All the threads I come across either dont work, skip some step that seems obvious to the writer or assume I know something that I haven't yet discovered. 

Thank you.

Taylor

---

### Post by jaa75 on 2010-09-23
I have a similar problem with my new System76 laptop.  At first, wireless worked fine, I could get to the internet, see other computers and the printer on my home network, but all at once, it stopped connecting automatically, and when I went through the manual setup, it claimed to be connected, but could not see the internet or the home network.

The Ubuntu version is 10.04, the CPU a 4-core AMD.

Can someone tell me how to re-install?  The laptop came without an installed system, but with a setup program that once I chose time zone and language, then proceeded to install 10.04.   How can I trigger a re-install??

jaa75

---

### Post by xcrogers on 2010-09-23
here is some info as I attempt to figure out what is going on:

taylor@taylor-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=19/70  Signal level=-83 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:7
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

taylor@taylor-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:e4:dd:eb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:4c000000-4c01ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:6e:6c:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b



taylor@taylor-laptop:~$ sudo iwlist eth1 auth
eth1      Authentication capabilities :
        WPA
        CIPHER-TKIP
          Current Key management :
          Current TKIP countermeasures : no
          Current Authentication algorithm :
        open


so just to be clear.. I can find (see the available networks) but I am continually prompted to enter my password. and yes, I have checked it several times and my MacBook Pro directly to my left has no problem connecting.

---

### Post by xcrogers on 2010-09-28
oh common.. there has got to be someone out there that can offer something....

---

