---
title: "wireless issues"
date: 2010-01-10
forum: General Help
---

### Post by yobird42 on 2010-01-10
I just installed 9.10 and am attempting to get my linksys wusb54gc v3 working.

it's recognized by the system as 

```
Bus 001 Device 003: ID 1737:0077 linksys
```

a wireless device appears in the list

```
wlan0     Link encap:Ethernet  HWaddr 00:23:69:d9:cd:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I am unable to scan for networks or manual input an essid.

I think it may be an issue of interface naming as sudo cat /etc/network/interfaces gives me
```
auto lo
iface lo inet loopback
```
but wlan0 does not show up

any help solving this would be greatly appreciated.

---

### Post by yobird42 on 2010-01-10
Any help?

---

### Post by yobird42 on 2010-01-10
bump again

---

### Post by SecretCode on 2010-01-10
If you're using Network Manager (as you would by default), the interface should not appear in /etc/network/interfaces, so that's fine.

Can you find the network manager icon in the top panel and right-click - firstly, do you have an entry "Enable wireless" and is it ticked?

Secondly can you click "Edit Connections..." and go to the wireless tab. Is there anything listed there?

eta: bad form to bump so quickly.

---

### Post by warfacegod on 2010-01-10
You may need to activate your wireless driver in Admin.> Hardware Drivers

---

### Post by yobird42 on 2010-01-10
First off, I apologize for the bumping I'm really impatient.

yes, wireless is enabled. I can type in my network name and it says it's searching, but the light on my adapter doesn't come on and nothing happens. There are no drivers to enable in the proprietary drivers menu. Is the drivers the problem?

---

### Post by yobird42 on 2010-01-10
I did some research and found this [http://ubuntuforums.org/showpost.php?p=8418039&postcount=182]("http://ubuntuforums.org/showpost.php?p=8418039&postcount=182")
I followed those instructions, however blacklisting drivers seemed to take me backwards and I couldn't even right click enable wireless anymore.

I have no idea what to do as I have exhausted all the options I researched, I'm not even sure if it's possible to get this thing working. 

The only thing left is to try ndiswrapper and I'd like to avoid that route if at all possible.

---

### Post by warfacegod on 2010-01-10
> I have no idea what to do as I have exhausted all the options I researched, I'm not even sure if it's possible to get this thing working.

It is possible but pretty unlikely that you *_won't_* get it working. Don't get discouraged too soon.

Make sure your computer is updated and try Hardware Drivers again.

> I am unable to scan for networks or manual input an essid.

Are you scanning with *sudo iwlist scanning* in a Terminal?

Use the code: lspci to find out what wireless chipset you have and search for that in the forums. Here's mine as an example.

```
warfacegod@warfacegod-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)
02:04.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:04.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:06.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
```

Notice the lines where it says ethernet controller. The second where it says Atheros blah blah is my wireless.

So, if I were to search for mine, I would use *Atheros Communications Inc. AR5211 802.11ab* first then just *AR5211 802.11ab*.

---

### Post by warfacegod on 2010-01-10
This site will be a good tool once you find your chipset:

[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

---

### Post by yobird42 on 2010-01-10
I already posted that. ```
Bus 001 Device 003: ID 1737:0077 linksys
``` It uses ralink rt2x00 drivers if I remember correctly.

sudo iwlist scan was the first thing I tried. It returned no results.

the link you posted says this about my device:

Linksys	 802.11g	 WUSB54GC v. 3	 man: 1737 dev: 0077	 USB	 rt2x00	green	 Driver available from manufacturer: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) , or [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) ; Ralink sent another driver that would compile (ver 2.1.0.0). **Will not work with WEP or WPA.**

Does this mean I can't have network security?

---

### Post by warfacegod on 2010-01-10
> **yobird42 said:**
> I already posted that. ```
Bus 001 Device 003: ID 1737:0077 linksys
``` It uses ralink rt2x00 drivers if I remember correctly.

sudo iwlist scan was the first thing I tried. It returned no results.

the link you posted says this about my device:

Linksys	 802.11g	 WUSB54GC v. 3	 man: 1737 dev: 0077	 USB	 rt2x00	green	 Driver available from manufacturer: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) , or [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) ; Ralink sent another driver that would compile (ver 2.1.0.0). **Will not work with WEP or WPA.**

Does this mean I can't have network security?

Yes. It looks like that driver will not support encryption. It would not surprise me, however, if someone has figured out a way around that.

You might consider getting a different wireless card.

---

### Post by yobird42 on 2010-01-10
> **warfacegod said:**
> Yes. It looks like that driver will not support encryption. It would not surprise me, however, if someone has figured out a way around that.

You might consider getting a different wireless card.


I'm not ready to give up just yet, I'll keep searching. Just in case, do you know of any usb adapters that work out of box plug n play no frustrations?

---

### Post by warfacegod on 2010-01-10
Not off hand no. I almost never use them, sorry.

---

### Post by warfacegod on 2010-01-10
This looks like it might be a good place to start:

[http://www.linuxemporium.co.uk/products/wireless/]("http://www.linuxemporium.co.uk/products/wireless/")

---

