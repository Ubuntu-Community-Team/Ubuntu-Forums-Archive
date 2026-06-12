---
title: "ubuntu wireless switch"
date: 2009-10-30
forum: General Help
---

### Post by su-37 on 2009-10-30
Hey, i have somehow managed to switch the wireless of my laptop off. Is there a setting i can use to turn it back on?
james@james-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by lidex on 2009-10-30
Do you have network-manager enabled in system>preferences>startup applications? If not enable it and reboot.

---

### Post by lidex on 2009-10-30
When/if enabled, right-click icon in notification area and place a check in box for "enable networking"

---

### Post by su-37 on 2009-10-30
Yes the network manager is enabled.

---

### Post by lidex on 2009-10-30
Most laptops have a hardware switch for wifi. Look closely at front edge and on both sides.Could very well be a slider. Also, recent models have a touch-type switch. Took me a minute to find on my new HP. Should have a green light/icon/led when enabled - not red.

---

### Post by su-37 on 2009-10-31
I dont think the hard wire switch is important as with my laptop it seems to be irrelevant and has never worked under linux. The wireless has and as i was typing this the wireless came back on. ? Thanks for the help anyway.

---

### Post by su-37 on 2010-02-12
hey its me again. Upgraded to 9.04 then 9.10 in a bid to get wireless working and it seems not to want to. this is the information i have managed to gather. 
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:57:b6:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.9 latency=0 multicast=yes
       resources: irq:28 ioport:3000(size=256) memory:93010000-93010fff(prefetchable) memory:93000000-9300ffff(prefetchable) memory:93020000-9303ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:24:83:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:95100000-9510ffff








james@james-laptop:~$ iwconfig
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




Now i think it may have something to do with the power management being off. Any ideas on how to turn it back on?

---

### Post by lidex on 2010-02-12
You **_still_** have no wireless? Go here, do this:
[http://ubuntuforums.org/showthread.php?t=1233770]("http://ubuntuforums.org/showthread.php?t=1233770")

---

