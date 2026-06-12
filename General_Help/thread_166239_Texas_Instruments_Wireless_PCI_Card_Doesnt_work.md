---
title: "Texas Instruments Wireless PCI Card Doesnt work"
date: 2006-04-26
forum: General Help
---

### Post by neoroses on 2006-04-26
Hi guys, i have a texas instruments ac111 wireless pci card which i jus can't get to work with ubuntu. Ive got the build essentials, and there are the needed drivers. the card shows up in networking and all my info is correct. IP,DNS,DG etc but it just will not connect. in firefox when trying to load a page the cursor has the loading symbol and it ses loading [www.google.com](www.google.com) etc. but never loads.

Also when trying to delete and move folders it ses i do not have permission to do the requested option. :(

Cheers

---

### Post by ubuntuuser on 2006-04-26
Can you ping your router? Please provide the output of iwconfig, ifconfig and route.

---

### Post by neoroses on 2006-04-26
Cheers for the reply. I can't ping my router, and when i try n access it through firefox it says connection refused. here is the info you asked for:

matt@USR8054:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"USR8054"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

matt@USR8054:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:67663 (66.0 KiB)  TX bytes:67663 (66.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:E0:98:D7:60:78
          inet addr:192.168.123.101  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:98ff:fed7:6078/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22

matt@USR8054:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.123.0   *               255.255.255.0   U     0      0        0 wlan0


Thanks for the help

---

### Post by ubuntuuser on 2006-04-26
So your system does recognize your card. It looks like a config problem. Do you use WPA to secure your network? If so, search for threads regarding wpa_supplicant, I can't help you then, because I have a pretty old router at home that just does WEP. Did you provide the WEP key? Enter it again to be sure you didn't make a mistake when entering it.
The iwconfig and ifconfig command tells us that your card seems to be correctly configured, but doesn't connect to your access point. If it did, we could see the AP MAC instead of 00:00...
My best guess is that you 
a) use WPA -> you'll need the mentioned wpa_supplicant
b) made a typing mistake when entering the WEP or didn't enter one -> (re)enter the WEP

Furthermore, you didn't set up a gateway for outgoing connections. When I type route, this is what I get on my PC:

```
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
[COLOR=Red]default         192.168.0.54    0.0.0.0         UG    0      0        0 wlan0[/COLOR]

``` You need to type this: ```
sudo route add default gw router.IP.here.please
``` That will of course only help once you connected to your AP/router.

I wish you good luck and hope I was able to help. I'm going on holiday today, and my girlfriend will kill me if I touch a PC :-)

---

### Post by neoroses on 2006-04-27
I'm not using a WEP key, ok ill try setting up a gateway

---

