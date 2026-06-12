---
title: "Wifi Messed Up. AGAIN!!"
date: 2011-07-01
forum: General Help
---

### Post by parkerskouson on 2011-07-01
Ok... For the second time this week, my wifi failed. It says that the wireless networks is disabled. 10.10 if it makes any difference.

Please Help

Parker

---

### Post by linuxuser12345 on 2011-07-01
You may need to install the proper driver for your network card. Go to the Additional Drivers application and see if you can find anything, if not, install NDISGTK from the Ubuntu Software Center. Open the program, install the .exe file for the driver (you can find that on the manufacturer's website), extract it, find the .inf file, and insert the .inf file into NDISGTK (Windows Wireless Drivers Utility).

---

### Post by linuxuser12345 on 2011-07-01
If you need help along the way, just ask! :)

---

### Post by parkerskouson on 2011-07-01
Do you by chance know how to find what type of wireless card i have?? Btw it is a laptop.

---

### Post by linuxuser12345 on 2011-07-01
You will have to probably go through the terminal to find out. Sorry, but I am not too good at the terminal! :O
Just be patient, and someone knowing how to work with the terminal will help you ASAP!

---

### Post by parkerskouson on 2011-07-01
Cool. Thanks for the help.

---

### Post by linuxuser12345 on 2011-07-01
Can you post us the output of
```
ifconfig
``````
iwconfig
```and
```
lshw -C network
```?

---

### Post by parkerskouson on 2011-07-01
Here:


eth0      Link encap:Ethernet  HWaddr 00:1f:16:40:b0:30  
          inet addr:10.0.0.23  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe40:b030/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1165341 (1.1 MB)  TX bytes:200109 (200.1 KB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9512 (9.5 KB)  TX bytes:9512 (9.5 KB)




lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off




WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:40:b0:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=10.0.0.23 latency=0 multicast=yes
       resources: irq:43 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:55:99:38
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:92600000-9260ffff

---

### Post by linuxuser12345 on 2011-07-01
This is the information you need (extra-special information is in bold):
> **parkerskouson said:**
> 
       [B]description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.[/B]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:55:99:38
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       **configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg**
       resources: irq:17 memory:92600000-9260ffff

Luckily, I think I may be able to help you now! :)

---

### Post by linuxuser12345 on 2011-07-01
And, I think I may have already found the answer you need!
Go [here]("http://ubuntuforums.org/showthread.php?t=1434524"): [http://ubuntuforums.org/showthread.php?t=1434524](http://ubuntuforums.org/showthread.php?t=1434524)

---

### Post by parkerskouson on 2011-07-01
AWESOME!! So what do i need to do?

---

### Post by linuxuser12345 on 2011-07-01
Go to the Ubuntu Software Center, and look up "Windows Wireless Drivers". Install it.
*Now, just so you know ahead of time, this may not work, but it is worth a shot!*

Install the driver: [http://www.station-drivers.com/telechargement/atheros/wifi/atheros_wifi_9.2.0.310(www.station-drivers.com).exe](http://www.station-drivers.com/telechargement/atheros/wifi/atheros_wifi_9.2.0.310(www.station-drivers.com).exe)

Extract the .exe file, and begin searching for the famous .inf file. Once found:

Open up the Windows Wireless Drivers utility, and input the .inf file. Hit "install" or whatever and see what happens! (A restart may be required).

---

### Post by parkerskouson on 2011-07-01
That is the problem.i have done this..but the card it still turned off. It wont turn back on. Any other suggesstions? I will proceed and do this again anyway though.

---

### Post by linuxuser12345 on 2011-07-01
Um, have you tried clicking the Network button on the top and connect to your network? lol

You may need to go through your BIOS and make sure it is enabled.

---

### Post by parkerskouson on 2011-07-01
Ummm... what does this mean???



Archive:  /home/parker/Downloads/atheros_wifi_9.2.0.310([www.station-drivers.com).exe](www.station-drivers.com).exe)
[/home/parker/Downloads/atheros_wifi_9.2.0.310([www.station-drivers.com).exe]](www.station-drivers.com).exe])
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/parker/Downloads/atheros_wifi_9.2.0.310([www.station-drivers.com).exe](www.station-drivers.com).exe) or
          /home/parker/Downloads/atheros_wifi_9.2.0.310([www.station-drivers.com).exe.zip](www.station-drivers.com).exe.zip), and cannot find /home/parker/Downloads/atheros_wifi_9.2.0.310([www.station-drivers.com).exe.ZIP](www.station-drivers.com).exe.ZIP), period.

---

### Post by parkerskouson on 2011-07-01
Btw. This is when trying to extract the exe file.

---

### Post by wildmanne39 on 2011-07-02
Hi, please put these commands in a terminal
```
lspci -nn
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by linuxuser12345 on 2011-07-02
^do what he said, please^ :)

---

### Post by louisgonick on 2011-07-17
Hi I hope this is not too late. I have the same card, and it does not work very well with ubuntu. You need to turn it on manually.
I use this codes to turn it on:
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

sometimes you need to try many times.
I hope this helped ;)

---

