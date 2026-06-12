---
title: "can't connect to internet using eternet cable"
date: 2010-05-26
forum: General Help
---

### Post by Mr_Yaser on 2010-05-26
hi
 
i just install ubuntu in my HP pavilion dv6, but i noticed that i cant acces the network using ethernet. 
 
So, do i have to install a driver for my card ? or i have to do some stips to configer the connection ?
 
i am new in ubuntu and i don't know how to deal with this problem.
Any help ?
 
thanx in advance

---

### Post by dino99 on 2010-05-26
[http://www.google.com/search?hl=fr&lr=&tbo=p&tbs=qdr%3Ay&q=dv6%2Blucid&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=fr&lr=&tbo=p&tbs=qdr%3Ay&q=dv6%2Blucid&aq=f&aqi=&aql=&oq=&gs_rfai=)

sudo ifconfig wlan0 up
sudo iwlist scan

goto: System-->Admnistration--> hardware driver
and choose: broadcom STA

---

### Post by Mr_Yaser on 2010-05-26
thanx for the fast replay
i did what u asked me to do
but when i go to System-->Admnistration--> hardware driver 
there is no thing about broadcom STA
 
you may want to take a lock at the outpot of the commends i wrote in the terminal :
 
>  
yaser@Mr:~$ sudo iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wlan0 Scan completed :
Cell 01 - Address: 00:24:A1:78:98:49
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=24/70 Signal level=-86 dBm 
Encryption key:on
ESSID:"menatelecom"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000006cc50fb8
Extra: Last beacon: 3148ms ago
IE: Unknown: 000B6D656E6174656C65636F6D
IE: Unknown: 010882848B0C12961824
IE: Unknown: 030101
IE: Unknown: 200100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: DD0900037F01010000FF7F
IE: Unknown: DD0A00037F04010000000000
IE: Unknown: 0706555320010B1B
Cell 02 - Address: 00:1F:9F:EC:89:85
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=23/70 Signal level=-87 dBm 
Encryption key:off
ESSID:"Thomson049BF5"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=000000025522420e
Extra: Last beacon: 3132ms ago
IE: Unknown: 000D54686F6D736F6E303439424635
IE: Unknown: 010882848B962430486C
IE: Unknown: 030101
IE: Unknown: 2A0100
IE: Unknown: 2F0100
IE: Unknown: 32040C121860
IE: Unknown: DD060010180200F0
pan0 Interface doesn't support scanning.
 

---

### Post by bredman on 2010-05-26
Please clarify if you are having problems with a wired connection or a wireless connection.

If you want to use a wired connection, try disabling your wireless connection first.

---

### Post by inso_741 on 2010-05-26
> **dino99 said:**
> [http://www.google.com/search?hl=fr&lr=&tbo=p&tbs=qdr%3Ay&q=dv6%2Blucid&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=fr&lr=&tbo=p&tbs=qdr%3Ay&q=dv6%2Blucid&aq=f&aqi=&aql=&oq=&gs_rfai=)

sudo ifconfig wlan0 up
sudo iwlist scan

goto: System-->Admnistration--> hardware driver
and choose: broadcom STA

I don't think this will help you since you want to configure your ethernet and not wifi
run ifconfig if you see eth0 that means you don't need any driver your card's been detected
you then just need to configure it

---

### Post by warfacegod on 2010-05-26
Try right clicking the Network Applet on your panel and making sure that Enable Networking has a check next to it.

---

### Post by Mr_Yaser on 2010-05-28
> **inso_741 said:**
> 
run ifconfig if you see eth0 that means you don't need any driver your card's been detected
you then just need to configure it
 
 
when i run ifconfig, it gave me the outpot of two devices
one of them is [COLOR=red]lo [COLOR=black]and the other is[/COLOR] wlan0[/COLOR]

as i know wlan0 is for the wifi
so the lo for the wired network ?

---

### Post by dino99 on 2010-05-28
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

and look at ubuntuguide below

---

### Post by inso_741 on 2010-05-28
run this and post the o/p here
```
ifconfig -a
```

---

### Post by Mr_Yaser on 2010-05-28
> **inso_741 said:**
> run this and post the o/p here
```
ifconfig -a
```


here is the o/p
> yaser@Mr:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160138 (160.1 KB)  TX bytes:160138 (160.1 KB)

pan0      Link encap:Ethernet  HWaddr aa:f6:d4:54:7b:d3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:cf:6e:0e  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:faff:fecf:6e0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47288841 (47.2 MB)  TX bytes:4755819 (4.7 MB)


---

### Post by inso_741 on 2010-05-28
what ethernet adapter do you have?
it seems it hasn't been detected...

also try ```
sudo ifconfig eth0 up
```

---

### Post by Mr_Yaser on 2010-05-29
> **inso_741 said:**
> what ethernet adapter do you have?
it seems it hasn't been detected...
 
also try ```
sudo ifconfig eth0 up
```
 
 
here is the o/p :-
 
```
yaser@Mr:~$ sudo ifconfig eth0 up
SIOCSIFFLAGS: Cannot assign requested address
```

---

### Post by inso_741 on 2010-05-29
run 'lspci' does it list your ethernet adapter?
if it doesnt then you need to install drivers for you card
give us information about your card and we'll help you find drivers

---

### Post by Mr_Yaser on 2010-05-29
> **inso_741 said:**
> run 'lspci' does it list your ethernet adapter?
if it doesnt then you need to install drivers for you card
give us information about your card and we'll help you find drivers
 
 
HERE IS THE O/P
 
```

yaser@Mr:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
[COLOR=red]03:[/COLOR][COLOR=red]00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)[/COLOR]
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```
 
i think the red colour is my ethernet card
am i right ?
but still dosn't work

---

### Post by inso_741 on 2010-05-29
[here's]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false") your driver

i think there is a bug with the default driver

if you need help installing it look [here]("http://www.slax.org/forum.php?action=view&parentID=49681&highlight=realtek")


hope it helps

---

### Post by Mr_Yaser on 2010-05-29
thanx a lot
i will try installing the driver now
thanx

---

### Post by Mr_Yaser on 2010-05-30
I installed the driver
but unfortuntly it seams like it dosn;t work for me !
any help ?

---

### Post by inso_741 on 2010-05-30
post 'ifconfig' o/p again

---

