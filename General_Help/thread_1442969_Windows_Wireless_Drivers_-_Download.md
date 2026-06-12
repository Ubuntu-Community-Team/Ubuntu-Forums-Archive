---
title: "Windows Wireless Drivers - Download"
date: 2010-03-30
forum: General Help
---

### Post by Dunk1994 on 2010-03-30
Hi,

I need to download 'Windows Wireless Drivers' from the Ubuntu Software Centre but I cannot as I do not have an Ubuntu computer with an internet connection (hence the need for the application). 

Would it be possible for someone to email it to me so I may put it onto a removable storage device and install it onto my Ubuntu computer?

If not; are there any alternative solutions (other than Madwifi).

Thanks! ;)

---

### Post by bobcollard on 2010-03-30
> **Dunk1994 said:**
> Hi,

I need to download 'Windows Wireless Drivers' from the Ubuntu Software Centre but I cannot as I do not have an Ubuntu computer with an internet connection (hence the need for the application). 

Would it be possible for someone to email it to me so I may put it onto a removable storage device and install it onto my Ubuntu computer?

If not; are there any alternative solutions (other than Madwifi).

Thanks! ;)
You don't need a Ubuntu system to download Windows Driver from Ubuntu Software Center.  I assume you are using windows now to write this?  Just Google the site and go there.

---

### Post by zipperback on 2010-03-30
You might not actually need to use a Windows driver for wifi.

Do you know what chipset you have for wifi?

Perhaps you could provide the following information.

Open a terminal window with Applications -> Accessories -> Terminal

And then issue the following command:

```

lspci

```

Then provide the output here.

Perhaps you could also provide the output from the following command as well:

```

lsusb

```

- zipperback
:popcorn:

---

### Post by Dunk1994 on 2010-03-31
Thanks for your response,

When I typed 'lspci':

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

and when I typed 'lsusb':

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Thanks

---

### Post by Dunk1994 on 2010-03-31
In response to the reply:

> **bobcollard said:**
> You don't need a Ubuntu system to download Windows Driver from Ubuntu Software Center.  I assume you are using windows now to write this?  Just Google the site and go there.

If you try to access the Ubuntu Software Center web address, it says: 
**'You don't seem to be running Ubuntu'**

And nothing more...

---

### Post by bobcollard on 2010-03-31
> **Dunk1994 said:**
> In response to the reply:



If you try to access the Ubuntu Software Center web address, it says: 
**'You don't seem to be running Ubuntu'**

And nothing more...
Sorry, maybe zipperback can help?

---

### Post by zipperback on 2010-04-21
Ok. I believe that you should be able to get your wifi up and running.

Your system has the following wifi chipset:
```
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```

Try this.

Click "System" -> "Administration" -> "Hardware Drivers".

There should be a wifi driver available from there.

Activate it and then reboot.

You shouldn't need to use the windows ndis driver wrapper.

Could you please also tell me which specific ubuntu installation you are running? As well as if it is the 32bit or 64bit version.

- zipperback

---

### Post by zipperback on 2010-04-21
Please also provide the output from the following commands:

```

ifconfig

```

```

iwconfig

```

Thanks.
- zipperback
:popcorn:

---

### Post by Dunk1994 on 2010-04-21
Hi, Thanks for getting back to me :KS

There doesn't seem to be any drivers as, after following your instructions, the following message appeared: 'No proprietary drivers are in use on this system' and the boxes below were empty.

I am running the 32bit version of 9.10 Karmic Koala.

When I entered: 'ifconfig' the following appeared:

   eth0      Link encap:Ethernet  HWaddr 00:c0:9f:90:43:24  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:19 Base address:0x2000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:cf:ea:00  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  wmaster0  Link encap:UNSPEC  HWaddr 00-0E-9B-CF-EA-00-00-00-00-00-00-00-00-00-00-00  
            UP RUNNING  MTU:0  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  

And when I entered: 'iwconfig' the following appeared:

   lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  wmaster0  no wireless extensions.
  
   
   
  wlan0     IEEE 802.11bg  ESSID:""  
  
            Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
  
            Tx-Power=20 dBm   
  
            Retry  long limit:7   RTS thr:off   Fragment thr:off
  
            Power Management:off
  
            Link Quality:0  Signal level:0  Noise level:0
  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0


thanks!

---

### Post by Dunk1994 on 2010-04-21
sorry, the surprised smiley is a colon followed by a zero, for some reason it came out like that!

---

### Post by maxrpowell on 2010-04-21
Do you have a landline you can use? Thats how I always get my WiFi drivers. Do you have a dual install? If so you can download the drivers (just google for the ones you need). You can install them in ubuntu from a flash drive maybe.

---

### Post by shaka_zulu on 2010-04-21
[http://www.ubuntu-how-to.com/2010/04/ubuntu-driver-ndiswrapper-wifi-card.html](http://www.ubuntu-how-to.com/2010/04/ubuntu-driver-ndiswrapper-wifi-card.html)

try with this tutorial.

---

### Post by Dunk1994 on 2010-04-25
I'm afraid the tutorial didn't help for various reasons... And having tried to plug my computer directly into the phone line I discovered that the Ethernet is faulty too!

---

### Post by zipperback on 2010-04-28
> **Dunk1994 said:**
> And having tried to plug my computer directly into the phone line I discovered that the Ethernet is faulty too!

You need to fix the faulty hardware in your system first as this could be causing you additional problems as well.

- zipperback
:popcorn:

---

### Post by MattM11 on 2010-04-28
The way I managed to install Windows Wireless Drivers without an Internet connection was through this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Scroll down to the Installing Packages section and download the three packages (ndiswrapper-common, ndiswrapper-utils and ndisgtk) to a usb drive. Then you can transfer them to your Ubuntu drive and install them (in the order listed above). 

Windows Wireless Drivers should then appear in System - Administration menu.

---

### Post by klemes on 2010-04-28
I think your wireless interface (wlan0) is already configured judging by the output of ifconfig & iwconfig commands.I think that you only have to supply your network information in the network-manager and you are all set.
Type ```
lswh -C Network
``` and in the last line see what driver is in use to confirm the above.
Also I maybe misunderstood here but the ethernet cable you plug it into your router and not the phone-line directly:P
Give both a shot and report back...
:popcorn::guitar:

---

### Post by Dunk1994 on 2010-04-29
Thanks again for your help! 

According to 'Synaptic Package Manager' the Ndiswrapper is already installed in the system but the internet still doesn't work. And Terminal says that the code 'lswh -C Network' does not exist...

:(

---

### Post by shaka_zulu on 2010-04-29
You wireless will not work only if your ndiswrapper is installed. You need to use it in order to make your wireless work.

---

