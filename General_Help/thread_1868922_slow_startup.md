---
title: "slow startup"
date: 2011-10-25
forum: General Help
---

### Post by mdt90 on 2011-10-25
Hi,

I have installed ubuntu 10.10 on my laptop.whenever i boot in ubuntu, initially i see the curser blinking for a long time, then it throws an error:
MCU hardware request failed....
and finally it starts up.Once started,it works fine!!

can anyone suggest me tips to speed up the boot process?

thanks in advance

---

### Post by mdt90 on 2011-10-25
to be specific,the message displayed is -

rt2800 pi_mcu_status Error: MCU request failed,no response from hardware.

which is followed by the boot process ..

---

### Post by ofnuts on 2011-10-25
> **mdt90 said:**
> to be specific,the message displayed is -

rt2800 pi_mcu_status Error: MCU request failed,no response from hardware.

which is followed by the boot process ..
The RT2800 is a WiFi interface chip. See [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Did you configure it by mistake?

---

### Post by Spyderkid on 2011-10-25
if you can go into recovery mode and use the root command shell to run... fsck

---

### Post by mdt90 on 2011-10-25
> **ofnuts said:**
> The RT2800 is a WiFi interface chip. See [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Did you configure it by mistake?

read the page info..unknowingly, i may have configured  it.but my wifi is working properly.. anyways now what should be done for a normal startup?

---

### Post by mdt90 on 2011-10-25
> **Spyderkid said:**
> if you can go into recovery mode and use the root command shell to run... fsck

ran fsck in shell from recovery mode..it says "drive already mounted..it will cause severe damage to file system"..as i am a beginner,can you please elaborate the procedure?

---

### Post by ofnuts on 2011-10-25
> **mdt90 said:**
> read the page info..unknowingly, i may have configured  it.but my wifi is working properly.. anyways now what should be done for a normal startup?Run "lspci" (no arguments) to see what kind of Wifi chip support your system really has. The output is something like this
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
[I]<some lines removed>
[/I]00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
*<some more lines removed>*
[COLOR=Red]03:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
[/COLOR]0d:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)

```in which you have to find which line seems to be the Wifi chip. You can also run "lshw" and check the *-network parts:
```

           *-network
                description: Wireless interface
                product: WiFi Link 6000 Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 35
                serial: 00:27:12:4d:ec:07
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:31 memory:f2400000-f2401fff

```

@spyderkid: I don't see the relevance of fsck?

---

### Post by mdt90 on 2011-10-25
output of lspci:
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9200M G] (rev b1)
07:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

output of lshw:
*-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 40:61:86:15:6d:91
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:22 memory:e4688000-e4688fff ioport:f110(size=8) memory:e4687000-e46870ff memory:e4686000-e468600f

---

### Post by ofnuts on 2011-10-25
> **mdt90 said:**
> output of lspci:
[COLOR=Red]07:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe[/COLOR]

OK, that sort of explains why there is the wrong driver installed. Right brand, wrong chip. The output of lshw should have a second *-network, the one you list is the Ethernet connection. So yes, you can attempt to remove the driver for the RX2800 without removing the one for the RT3090, but doing this properly is getting a bot over my level of expertise.

---

### Post by mdt90 on 2011-10-25
how did you figure out the wrong driver problem from the output?
so how do i remove the driver and install the proper one for my wifi?

---

### Post by ofnuts on 2011-10-25
> **mdt90 said:**
> how did you figure out the wrong driver problem from the output?
so how do i remove the driver and install the proper one for my wifi?
Oops. I may ahave been a bit quick here. The RT2x00 project eventually got merged in the general Linux kernel, so the wiki Google leads to is a bit out of date, and your wifi chip may be handled by a more recent version of the same driver. But then you have to find out why this module thinks you have an RT2x00 chip. What is the hardware? Laptop (brand/model)? desktop (brand/model or motherboard manufacturer/model)?

---

### Post by varunendra on 2011-10-26
@mdt90,
Please post the outputs of:
```
sudo lspci -nnk | grep -iA2 net
```
and 
```
lsmod | grep -iE "rt2|rt3"
```

Please wrap each set of outputs in 'code' tags to retain their formatting and thus make them more readable. To do so, click on the **#** symbol at the top of the edit box in which you write your posts. It will auto-generate [noparse]```
..and..
```[/noparse] tags. Now just copy-paste your outputs in-between those tags.

---

### Post by mdt90 on 2011-10-28
> **ofnuts said:**
> Oops. I may ahave been a bit quick here. The RT2x00 project eventually got merged in the general Linux kernel, so the wiki Google leads to is a bit out of date, and your wifi chip may be handled by a more recent version of the same driver. But then you have to find out why this module thinks you have an RT2x00 chip. What is the hardware? Laptop (brand/model)? desktop (brand/model or motherboard manufacturer/model)?

The laptop model is MSI T4300 (2.10 Ghz Dual Core)

---

### Post by mdt90 on 2011-10-28
@varunendra

outputs -
```

sudo lspci -nnk | grep -iA2 net
[sudo] password for mdt: 
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:101a]
    Kernel driver in use: forcedeth
--
07:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:6891]
    Kernel driver in use: rt2800pci


```

```

lsmod | grep -iE "rt2|rt3"
rt2860sta             504366  0 
rt2800pci               8852  0 
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  2 rt2860sta,rt2800pci
rt2x00lib              27307  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231927  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              144822  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2800pci


```

---

### Post by varunendra on 2011-10-29
> **mdt90 said:**
> 
```

07:00.0 Network controller [0280]: RaLink [COLOR=Red]**RT3090**[/COLOR] Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:6891]
    Kernel driver in use: **rt2800pci**


``````

lsmod | grep -iE "rt2|rt3"
rt2860sta             504366  0 
[COLOR=Red][B]rt2800pci               8852  0 
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci[/B][/COLOR]
crc_ccitt               1351  2 rt2860sta,rt2800pci[COLOR=Red][B]
rt2x00lib              27307  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231927  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              144822  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2800pci[/B][/COLOR]

```
Wow! Lots of rt's there :)
I 'believe' (and I may be wrong) that it is only rt2860 and crc_ccitt that need to be there. As a test, please do this to see if it improves or worsens:
```
sudo su
modprobe -r rt2800pci
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```
Then restart system and check
```
lsmod | grep rt2
``` to see if rt2800pci or any of the red ones are still there. Notice the performance difference (if any) as well.

---

### Post by mdt90 on 2011-11-12
[QUOTE=varunendra;11405658]Wow! Lots of rt's there :)
I 'believe' (and I may be wrong) that it is only rt2860 and crc_ccitt that need to be there. As a test, please do this to see if it improves or worsens:
[CODE]sudo su
modprobe -r rt2800pci
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit

Sorry for the late reply..
Well,I tried executing the above modprobe command but after pressing enter my computer hanged.

---

### Post by mdt90 on 2011-11-12
> **varunendra said:**
> Wow! Lots of rt's there :)
I 'believe' (and I may be wrong) that it is only rt2860 and crc_ccitt that need to be there. As a test, please do this to see if it improves or worsens:
```
sudo su
modprobe -r rt2800pci
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Then restart system and check
```
lsmod | grep rt2
``` to see if rt2800pci or any of the red ones are still there. Notice the performance difference (if any) as well.

Sorry for the late reply..
Well,I tried executing the above modprobe command but after pressing enter my computer hanged.

---

