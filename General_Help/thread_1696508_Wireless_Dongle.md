---
title: "Wireless Dongle"
date: 2011-02-27
forum: General Help
---

### Post by pod25 on 2011-02-27
I have 2 computers, both running Ubuntu 10.10
I purchased a TP-LINK Wireless Adaptor model number: TL-WN321G

On my main computer (Acer Laptop) I plugged the dongle into the usb port and Ubuntu picked it up straight away and connected, so it worked straight from the box.

I bought the dongle for my car PC, running Ubuntu 10.10
I then plugged the dongle into my car PC, but nothing, it was not recognised.
Even though Ubuntu came bundled with the correct driver files found in /lib/firmware/zd1211 I manually updated them from the latest driver download, but still nothing.

How can I get my dongle to work ?
I'm guessing I have missed something, because the dongle worked straight from the box on my laptop.

---

### Post by rolandrock on 2011-02-28
Check dmesg and /var/log/syslog for errors on the car pc.

With the dongle plugged in, compare the outputs of these commands from the different computers:
> lsusb
lsmod

This may help isolate the problem.

---

### Post by pod25 on 2011-02-28
> **rolandrock said:**
> Check dmesg and /var/log/syslog for errors on the car pc.

With the dongle plugged in, compare the outputs of these commands from the different computers:


This may help isolate the problem.

Thanks for the reply.
Using lsusb, my wireless dongle showed up.

However, I think I have figured out the problem ,but am not sure how to fix.
When I installed (usb bootable stick) it knew I had no ethernet card or dongle, hence I had no internet, so the drivers would not have been activated.
Using the Additional Drivers option won't work, because the system has no internet and I can not plug a ethernet cable in (its a car PC)

How do I manually activate the drivers ?

---

### Post by pod25 on 2011-03-01
Any takers on this.
It is really bizzare, the usb dongle shows up when using lsusb, but yet it is not working.
I have manually added my network and assigned a static IP address.

All the driver files are there.
It is as if I need to activate the dongle.

I know the dongle works, because I plugged into my laptop, which is also running Ubuntu 10.10 and it worked instantly.

And as I have stated, I can't use the Additional Drivers option.

---

### Post by Topsiho on 2011-03-01
You'll have to wait until someone comes up with a better reply than this one :)

In the mean time you could experiment, using your USB-stick from which you installed Ubuntu 10.10 as a LiveCD (a LiveStick?), with the dongle inserted (the PC has two USB-ports?), and try whether the dongle is found, and works.

If it is and does, or even when not, you could try to reinstall with the dongle present in the car PC, and see whether it now works OK.

The reason I find this answer a little absurd, is that the problem is better solved without reinstalling the OS.

Topsiho

---

### Post by pod25 on 2011-03-01
Re-installation is not an option.
The first time I installed, my touch screen did not work, the second time I installed it worked, so I don't want to take the risk of breaking my touch screen.

---

### Post by pod25 on 2011-03-06
I have now tried using the NDISWRAPPER and the windows driver for my dongle.

Using ndiswrapper -l tells me the driver is installed and my dongle is present.
I have loaded the driver into memory depmod -a
But still nothing.

The dongle works perfectly, I tested on my laptop which also runs Ubuntu 10.10 and when I plug the dongle in, it works first time.

---

### Post by ugm6hr on 2011-03-06
Plug into laptop and post output from:
```
lshw -class network
```
Then do the same in car PC. This will indentify what driver is being used on laptop, and whether any drivers are in use on car PC.
If lsusb identifies the device, I presume there is no problem with the hardware.

---

### Post by pod25 on 2011-03-06
Results from the laptop lshw -class network

```
*-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:4d:83:4a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:2000(size=256) memory:e2003000-e2003fff memory:48000000-4801ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e2004000-e2005fff
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:59:63:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic firmware=N/A ip=192.168.0.25 link=yes multicast=yes wireless=IEEE 802.11bg
  [COLOR="Red"]*-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 74:ea:3a:89:80:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.25 multicast=yes wireless=Ralink STA[/COLOR]

```

The part in red is my usb dongle.

Results from the car computer lshw -class network

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:6e:cf:02
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:1000(size=256) memory:50100000-50100fff memory:50000000-5000ffff memory:50020000-5003ffff

```

---

### Post by Topsiho on 2011-03-06
Only thing that I can think of is that it's the hardware: possibly the USB-port of the car computer is not working.

If the dongle works with the same version of Ubuntu in the other computer, but not in the car computer, the problem is not the dongle, and also not the Ubuntu version, but the different hardware.

So you better check the USB-port first, or use another port, if there is one.

Topsiho

---

### Post by Spyderkid on 2011-03-06
Open a terminal and type in lsusb and look for the chipset can you tell me what it is please then i will tell you how to make it work.


also try inserting the installation CD and then do this...
```

cd /media/CD NAME
./configure
make
make install

```
if that doesn't work have a look for the text file on the CD and read it on how to install.

---

### Post by pod25 on 2011-03-06
> **Topsiho said:**
> Only thing that I can think of is that it's the hardware: possibly the USB-port of the car computer is not working.

If the dongle works with the same version of Ubuntu in the other computer, but not in the car computer, the problem is not the dongle, and also not the Ubuntu version, but the different hardware.

So you better check the USB-port first, or use another port, if there is one.

Topsiho

I have 4 on board USB 2 ports.
There are 2 spare ports, as the other 2 are for my touch screen monitor.

When I plug the dongle in ,the green light on the dongle lights up and when I do lsusb it shows up in the list, so the usb ports are working.

---

### Post by pod25 on 2011-03-06
> **Spyderkid said:**
> Open a terminal and type in lsusb and look for the chipset can you tell me what it is please then i will tell you how to make it work.

lsusb reports this :

ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

---

### Post by runeh76 on 2011-03-06
Have u seen this:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10388456]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10388456")

---

### Post by Topsiho on 2011-03-06
"When I plug the dongle in ,the green light on the dongle lights up and when I do lsusb it shows up in the list, so the usb ports are working."

Ok, the USB-port is OK, and the dongle is recognized and seems to be working: the green light lights up.

What can still be wrong now?

I have no experience with a wifi USB-stick, that is recognized, and of which the green light lights up, and still doesn't work, so let me guess:

Where is the car computer? Is it within the range of the wireless network? Does it see other networks? If you left click on the network icon, does it show the wlan interface? Can you take the car computer into the house (that is: out of the car?) ...

Sorry that I can not help you further with this,

Topsiho

---

### Post by pod25 on 2011-03-06
@Topsiho

The car pc is hard wired into the car, it would involve stripping half the car out to remove  :)

When I take my laptop out side, it reaches my router with ease and has a fairly good reception, the car is on my drive right outside the house.

So this dongle should reach easily.

If the dongle was trying to get a reception, the green light would flash telling me it is trying to do something, but it stays steady.

Also the lshw output showed it was not present !!

---

### Post by pod25 on 2011-03-06
> **Spyderkid said:**
> Open a terminal and type in lsusb and look for the chipset can you tell me what it is please then i will tell you how to make it work.


also try inserting the installation CD and then do this...
```

cd /media/CD NAME
./configure
make
make install

```
if that doesn't work have a look for the text file on the CD and read it on how to install.

I installed Ubuntu using a usb bootable stick, as my car pc has no cd drive.

---

### Post by runeh76 on 2011-03-06
Did u read earlier link..? There is driver, what i think u need.

---

### Post by Topsiho on 2011-03-06
The reason I asked whether the car computer could be removed from your car is that a car is a Faraday cage, which means that electromagnetic radiation cannot reach the interior of the car from outside (which is why you are safe inside your car during a thunderstorm (as long as you don't park it against a tree or so)). So the car computer needs an outside  antenna to pick up a radio signal, just as your car radio does.

Why lshw doesn't show your dongle I don't know, as the dongle seems to be recognized, and the green light is on.

Topsiho

---

### Post by pod25 on 2011-03-06
> **Topsiho said:**
> The reason I asked whether the car computer could be removed from your car is that a car is a Faraday cage, which means that electromagnetic radiation cannot reach the interior of the car from outside (which is why you are safe inside your car during a thunderstorm (as long as you don't park it against a tree or so)). So the car computer needs an outside  antenna to pick up a radio signal, just as your car radio does.

Why lshw doesn't show your dongle I don't know, as the dongle seems to be recognized, and the green light is on.

Topsiho

I can understand your theory, but like I said, my laptop connects when sat in the car.

This is now driving me mad, how can it work on one computer but not another.
I could understand if both were running different operating systems, but they are both running the same  !!

---

### Post by Topsiho on 2011-03-06
I must say, it is beginning to drive me mad too.:confused:
Often the solution is very simple, but I am out of inspiration by now.

Sorry for this :(

I hope someone drops by for whom this is as simple as 10+10 (which is 100 as everyone knows).

Topsiho

---

### Post by pod25 on 2011-03-13
I'm still no closer to getting this to work.

Any one else have any suggestions ?

---

### Post by bkratz on 2011-03-13
Was just reading through the thread. Why do you think that it is the usb dongle connecting when using your laptop in the car?  When ugm6hr had you run the command in post 8 your output in post 9 shows a perfectly working BCM4318 wireless card. Maybe that is what is actually working?! You could tell by doing a

sudo iwlist scan

on the laptop and see whether wlan0 or wlan1 is actually producing the output. At least that would determine whether you should go through the long thread pointed to by runeh76.  If the information shows up on wlan0 you are actually using the BCM4318.

---

### Post by ugm6hr on 2011-03-13
> **bkratz said:**
> Was just reading through the thread. Why do you think that it is the usb dongle connecting when using your laptop in the car?  When ugm6hr had you run the command in post 8 your output in post 9 shows a perfectly working BCM4318 wireless card.

Agreed.
No driver is listed for wlan1 in lshw - as for why it has the ip (as does wlan0), I'm uncertain.

---

### Post by pod25 on 2011-03-13
Here is the output on my laptop when the usb dongle is plugged in using iwlist scan.

It shows both wlan0 and wlan1

I know the dongle is working just by seeing the green light flash the second I plug it in, where as on my car pc I get a steady green light which means it is doing nothing.

```
john@john-Aspire-3630:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:C1:4C:29
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"pod25music"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001507fdee6da
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A706F6432356D75736963
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001700000000000000000000000000000000000000
                    IE: Unknown: DD710050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800020088
                    IE: Unknown: DD090010180206F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409001700000000000000000000000000000000000000
          Cell 02 - Address: 00:22:3F:C5:EA:C0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"paulandneesha"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023912ec2183
                    Extra: Last beacon: 276ms ago
                    IE: Unknown: 000D7061756C616E646E6565736861
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:26:F2:82:DB:9E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"James"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a704a059fc
                    Extra: Last beacon: 956ms ago
                    IE: Unknown: 00054A616D6573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

wlan1     Scan completed :
          Cell 01 - Address: C0:3F:0E:C1:4C:29
                    Protocol:802.11b/g/n
                    ESSID:"pod25music"
                    Mode:Managed
                    Channel:9
                    Quality:89/100  Signal level:-55 dBm  Noise level:-83 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: C0:3F:0E:FE:92:00
                    Protocol:802.11b/g/n
                    ESSID:"Osman's"
                    Mode:Managed
                    Channel:1
                    Quality:31/100  Signal level:-77 dBm  Noise level:-83 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:26:F2:82:DB:9E
                    Protocol:802.11b/g
                    ESSID:"James"
                    Mode:Managed
                    Channel:6
                    Quality:37/100  Signal level:-75 dBm  Noise level:-83 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:22:3F:C5:EA:C0
                    Protocol:802.11b/g
                    ESSID:"paulandneesha"
                    Mode:Managed
                    Channel:11
                    Quality:31/100  Signal level:-77 dBm  Noise level:-83 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by pod25 on 2011-03-13
In /lib/firmware I can see the zd1211 folder. That is the driver folder for this dongle.

So it is /lib/firmware/zd1211/

How can I tell Ubuntu to load those drivers at start up.

Oh and they all have a funny file extension:

_ub
_uph
_uphm
_uphr
_ur

---

### Post by pod25 on 2011-03-13
> **pod25 said:**
> In /lib/firmware I can see the zd1211 folder. That is the driver folder for this dongle.

So it is /lib/firmware/zd1211/

How can I tell Ubuntu to load those drivers at start up.

Oh and they all have a funny file extension:

_ub
_uph
_uphm
_uphr
_ur

Ignore the above. I used hwinfo --usb to find what drivers and where they were on the laptop.
I have copied all the drivers onto my memory stick and shall manually add them onto the car pc.

Then I shall edit /etc/modules  to include the drivers at start up.

---

### Post by ugm6hr on 2011-03-13
I suspect, as you suggest, the problem here is that the car PC has no internet - hence it has not been updated, and cannot download drivers.
Manually installing is possible - but I'm not 100% certain what driver you need (lshw is unhelpful for this device).
Judging by other reports, this should work:
[http://ubuntuforums.org/showthread.php?p=10179313#post10179313](http://ubuntuforums.org/showthread.php?p=10179313#post10179313) (beware typo in step 12 - mentioned in later post)
Or, I think installing [http://packages.ubuntu.com/maverick/linux-backports-modules-compat-wireless-2.6.36-maverick-generic](http://packages.ubuntu.com/maverick/linux-backports-modules-compat-wireless-2.6.36-maverick-generic) may also work (as reported later in same thread).
Without existing ethernet - might be tricky - but should be doable by installing linux-backports-modules-compat-wireless-2.6.36-maverick-generic on the laptop, and then copying everything from /var/cache/apt/archives from laptop to same location on car PC, then installing on car PC.

---

### Post by bkratz on 2011-03-13
I would be real tempted to do a (just as an experiment)


sudo ifconfig wlan0 down
 
and then repeat  the sudo iwlist scan and see if the results attributed to wlan1 disappear also. You can alway bring it back up with
 sudo ifconfig wlan0 up

I really don't think that network manager can manage two wireless connections (could be wrong though!)  and since as ugm6hr stated above about the driver there seems to be confusion involved somewhere.

---

