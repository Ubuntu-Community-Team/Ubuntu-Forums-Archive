---
title: "The good old wireless problem.. plz any1"
date: 2012-01-06
forum: General Help
---

### Post by Clawsman on 2012-01-06
helo to all here!

First i would like to say i have done tonns of research before i post or ask.
But sadly i am out of ammo and need a lifting hand.

Its the popular intel pro ipw2200 wireless problem.

Indeed i did my research i downloaded the 3.1 firmware and copy it into /lib/firmware/.. and there it was.. my wireless worked!
After some tweeking i wanted to do an apt-get update... after that.. my wireless did not show up in Wicd network manager.

I have try'd everything... even formated (gparted) reinstalled 4 times and repeated my 3.1 firmware copy to make it work again.... guess what.. nothing works again.

this is what i am getting...

root@bt:~# dmesg | grep ipw
[   15.002828] libipw: 802.11 data/management/control stack, git-1.1.13
[   15.002836] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.284687] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   15.284696] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.284863] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.284910] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.028746] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)


firmware looks in place

root@bt:~# ls -al /lib/firmware | grep ipw
-rw-r--r--  1 root root  191154 2009-03-11 21:17 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2009-03-11 21:17 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2009-03-11 21:17 ipw2200-sniffer.fw
-rw-r--r--  1 root root   12007 2009-03-11 21:17 LICENSE.ipw2200-fw

my eth1 shows up... when doing ifconfig

eth1      Link encap:Ethernet  HWaddr 00:13:xx:xx:68:42  
          inet6 addr: fe80::213:ceff:fece:6842/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10512 (10.5 KB)
          Interrupt:17 Base address:0x4000 Memory:dfbfd000-dfbfdfff 




and iwconfig shows......

root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Any help will be much appreciated!

---

### Post by xc3RnbFO8P on 2012-01-06
Did you use the wireless turn off/on button?
sorry for asking so stupid question  :)

Ps: is it a Medion laptop?

---

### Post by Clawsman on 2012-01-06
> **Ringi said:**
> Did you use the wireless turn off/on button?
sorry for asking so stupid question  :)

Ps: is it a Medion laptop?

lol... yes.. in fact i did try the wireless on/off button.. in my case is fn+F2... but nothing happened when i try turn it back on.
I have a dell inspiron.

---

### Post by xc3RnbFO8P on 2012-01-06
What is the output of
> sudo rfkill list all

---

### Post by Clawsman on 2012-01-06
root@bt:~# sudo rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

hei fra norge forresten:)

---

### Post by Clawsman on 2012-01-06
well.. i havent done much after posting this thread. but i suddenly wanted to do a ifconfig command. and now my eth1 doesnt shows up at all.


edited: allright... i just reboot and ifconfig shows eth1 again... same state though...

eth1      Link encap:Ethernet  HWaddr 00:13:xx:xx:68:42  
          inet6 addr: fe80::213:ceff:fece:6842/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2448 (2.4 KB)
          Interrupt:17 Base address:0xa000 Memory:dfbfd000-dfbfdfff

---

### Post by Clawsman on 2012-01-07
problem solved! :) i am posting using my wireless ;)
All i had to do was to go into Wicd preferences and add eth1 in the wireless field. and bamm! there it was again ;)

And Thank U @Ringi... for learning me the "sudo rfkill list all" command.. that came usefull to me..and will be usefull in the future :)

---

### Post by xc3RnbFO8P on 2012-01-07
You solved it yourself :)  
mark it as solved.

---

