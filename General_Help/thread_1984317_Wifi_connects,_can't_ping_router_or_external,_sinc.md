---
title: "Wifi connects, can't ping router or external, since 12.04"
date: 2012-05-21
forum: General Help
---

### Post by m0116815 on 2012-05-21
Hi all,

Since upgrading to 12.04 I've had the following happen on several networks. I am able to connect to the wireless network, and the network applet shows that I'm connected, but I have no internet nor local access. I am not able to ping the router.

The computer is a recent Dell Latitude E6220 and has no other issues. Wifi works under Win7.

```
$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.058 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.056 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.065 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.056/0.059/0.065/0.009 ms

$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

```

```
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 84:8f:69:f1:46:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2045816 (2.0 MB)  TX bytes:307437 (307.4 KB)
          Interrupt:20 Memory:e1c00000-e1c20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137622 (137.6 KB)  TX bytes:137622 (137.6 KB)

wlan0     Link encap:Ethernet  HWaddr 08:11:96:df:a0:2c  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a11:96ff:fedf:a02c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14266 (14.2 KB)  TX bytes:82010 (82.0 KB)

```

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Graymalkin"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:86:3B:B6:3F:E4   
          Bit Rate=117 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.

```

```

$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Graymalkin] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        08:11:96:DF:A0:2C

  Capabilities:
    Speed:           117 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    icsics2:         Infra, 1C:7E:E5:4C:82:AB, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    buh-buh:         Infra, 00:19:E3:FA:E7:2A, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    icsics:          Infra, 00:0F:CB:FC:87:0F, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WEP
    linksys:         Infra, 00:1E:E5:86:D8:DF, Freq 2437 MHz, Rate 54 Mb/s, Strength 12
    Toepick:         Infra, 00:18:F8:B9:AE:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA
    London3:         Infra, 00:21:29:C9:8C:55, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    flyingpanda:     Infra, 58:6D:8F:C9:3E:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    flyingpanda-guest: Infra, 58:6D:8F:C9:3E:E3, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    *Graymalkin:     Infra, 08:86:3B:B6:3F:E4, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    carlcap:         Infra, 28:CF:DA:B5:0E:23, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        84:8F:69:F1:46:F9

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off

```

---

### Post by m0116815 on 2012-05-21
Sorry, hit Send too soon... 

So it looks like I have an IP address, but no connectivity. The only thing in the previous post that looks out of place is the loopback in interfaces.

I am at a loss. Any ideas would be appreciated.

---

### Post by PTo on 2012-05-21
I'm trying for more than a week to get my internet back as well so I don't think I have the solution, however as far as I have seen in other posts the loopback in interfaces looks pretty normal. I have learned from other posts is that whatever is mentioned in interfaces is not managed by network manager.

I'm on a wired connection so I don't know if it is of any help but in [this thread]("http://ubuntuforums.org/showthread.php?t=1983054&page=2") you can find what they have advised me so far

---

### Post by RobertSwipe on 2012-05-22
Exactly the same problem here using a Dell E6320.

It happens mostly on my home network (Belkin router), and I can usually get around the problem by disconnecting from the wireless network and reconnecting.

I'm using 12.04 and Gnome Shell, if that's of any help.

---

### Post by JuhazOne on 2012-05-22
I may be having the same problem. My kubuntu network applet tells me that I'm connected to my wireless router fine and the signal strength is good but I can't connect to the internet. At first I also thought that I can't even ping the router, but apparently I can - I just have packet loss around 95 %. I can't resolve the hostname for [www.google.fi](www.google.fi). If I manually ping the ip address for [www.google.fi](www.google.fi) the ping sometimes goes through but there's still 95 % packet loss.

My laptop is Lenovo L520. The router in question is an Elisa Viihde router provided by my ISP. A wired connection to this router works fine and I also have no problems (of this sort) with the wireless connection at work.

I'm using Kubuntu 11.10. The kernel version is (uname -a prints):
Linux hostname 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

dmesg and /var/log/syslog keep printing stuff like this many times a minute:

```
May 22 23:24:31 hostname kernel: [ 1560.300773] userif-2: sent link up event.
May 22 23:24:31 hostname kernel: [ 1560.624307] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
May 22 23:24:33 hostname wpa_supplicant[1388]: Trying to authenticate with 00:23:08:cb:cc:28 (SSID='tietokone' freq=2462 MHz)
May 22 23:24:33 hostname wpa_supplicant[1388]: Trying to associate with 00:23:08:cb:cc:28 (SSID='tietokone' freq=2462 MHz)
May 22 23:24:33 hostname kernel: [ 1562.825789] wlan0: authenticate with 00:23:08:cb:cc:28 (try 1)
May 22 23:24:33 hostname kernel: [ 1562.827619] wlan0: authenticated
May 22 23:24:33 hostname kernel: [ 1562.828169] wlan0: associate with 00:23:08:cb:cc:28 (try 1)
May 22 23:24:33 hostname NetworkManager[1051]: <info> (wlan0): supplicant interface state: scanning -> associating
May 22 23:24:33 hostname kernel: [ 1562.831991] wlan0: RX ReassocResp from 00:23:08:cb:cc:28 (capab=0x411 status=0 aid=1)
May 22 23:24:33 hostname kernel: [ 1562.832000] wlan0: associated
May 22 23:24:33 hostname vmnet-natd: RTM_NEWLINK: name:wlan0 index:3 flags:0x00011003
May 22 23:24:33 hostname wpa_supplicant[1388]: Associated with 00:23:08:cb:cc:28
May 22 23:24:33 hostname vmnetBridge: RTM_NEWLINK: name:wlan0 index:3 flags:0x00011003
May 22 23:24:33 hostname kernel: [ 1562.842585] cfg80211: Calling CRDA for country: FI
May 22 23:24:33 hostname NetworkManager[1051]: <info> (wlan0): supplicant interface state: associating -> associated
May 22 23:24:33 hostname kernel: [ 1562.849876] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849887] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849893] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849899] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849905] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849911] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849916] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849923] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849928] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849934] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849940] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849946] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849951] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849958] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849963] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849969] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849974] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849981] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849986] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.849992] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.849997] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850004] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850009] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850015] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850020] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850027] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850032] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850039] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850044] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850050] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850055] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850062] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850067] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850073] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850078] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850085] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850090] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850096] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850101] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850108] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850113] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850119] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850124] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850131] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850136] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850142] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850147] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850154] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850159] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850165] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850170] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850177] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850182] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850188] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850193] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850200] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850205] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850211] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850217] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850223] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850228] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850235] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850239] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
May 22 23:24:33 hostname kernel: [ 1562.850246] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850251] cfg80211: Disabling freq 5745 MHz
May 22 23:24:33 hostname kernel: [ 1562.850254] cfg80211: Disabling freq 5765 MHz
May 22 23:24:33 hostname kernel: [ 1562.850258] cfg80211: Disabling freq 5785 MHz
May 22 23:24:33 hostname kernel: [ 1562.850262] cfg80211: Disabling freq 5805 MHz
May 22 23:24:33 hostname kernel: [ 1562.850265] cfg80211: Disabling freq 5825 MHz
May 22 23:24:33 hostname kernel: [ 1562.850275] cfg80211: Regulatory domain changed to country: FI
May 22 23:24:33 hostname kernel: [ 1562.850279] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 22 23:24:33 hostname kernel: [ 1562.850286] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850292] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850298] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
May 22 23:24:33 hostname kernel: [ 1562.850303] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
May 22 23:24:34 hostname NetworkManager[1051]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
May 22 23:24:34 hostname wpa_supplicant[1388]: WPA: Key negotiation completed with 00:23:08:cb:cc:28 [PTK=CCMP GTK=TKIP]
May 22 23:24:34 hostname wpa_supplicant[1388]: CTRL-EVENT-CONNECTED - Connection to 00:23:08:cb:cc:28 completed (reauth) [id=0 id_str=]
May 22 23:24:34 hostname vmnet-natd: RTM_NEWLINK: name:wlan0 index:3 flags:0x00011043
May 22 23:24:34 hostname vmnetBridge: RTM_NEWLINK: name:wlan0 index:3 flags:0x00011043
May 22 23:24:34 hostname vmnetBridge: Adding interface wlan0 index:3
May 22 23:24:34 hostname vmnetBridge: Started bridge wlan0 to virtual network 0.
May 22 23:24:34 hostname kernel: [ 1563.119807] /dev/vmnet: open called by PID 1671 (vmnet-bridge)
May 22 23:24:34 hostname kernel: [ 1563.119836] /dev/vmnet: hub 0 does not exist, allocating memory.
May 22 23:24:34 hostname kernel: [ 1563.119909] /dev/vmnet: port on hub 0 successfully opened
May 22 23:24:34 hostname kernel: [ 1563.119938] bridge-wlan0: device is wireless, enabling SMAC
May 22 23:24:34 hostname kernel: [ 1563.119947] bridge-wlan0: up
May 22 23:24:34 hostname kernel: [ 1563.119955] bridge-wlan0: attached
May 22 23:24:34 hostname NetworkManager[1051]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
May 22 23:24:34 hostname kernel: [ 1563.319844] userif-2: sent link down event.
```

I also have VMware player installed and a Windows 7 virtual machine with bridged networking. The virtual machine also has problems pinging the default gateway though it does get an ip address just fine and it knows the ip for the default gateway. (I didn't wait long enough to see if some packets go through - I assume they would.)

---

### Post by wildmanne39 on 2012-05-22
Hi m0116815, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by procfs on 2012-05-23
Hi there,
I have the same problem with lenovo e420 (using 12.04 LTS) :( any solution ?!?

---

### Post by RobertSwipe on 2012-05-23
Results from the commands requested:

```

Linux PowerRob 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:0492]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1321]
	Kernel driver in use: iwlwifi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 001 Device 004: ID 1bcf:2980 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 004: ID 0951:1607 Kingston Technology DataTraveler 100


wlan0     IEEE 802.11abgn  ESSID:"MyWifi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:75:AC:34:C3   
          Bit Rate=78 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:75   Missed beacon:0


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


Module                  Size  Used by
uas                    18180  0 
usb_storage            49198  1 
ip6table_filter        12815  0 
ip6_tables             27864  1 ip6table_filter
ebtable_nat            12807  0 
ebtables               30984  1 ebtable_nat
ipt_MASQUERADE         12759  3 
iptable_nat            13229  1 
nf_nat                 25891  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  4 iptable_nat,nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  1 
nf_conntrack           81926  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             12576  2 
xt_CHECKSUM            12549  1 
iptable_mangle         12734  1 
xt_tcpudp              12603  5 
iptable_filter         12810  1 
pci_stub               12622  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  12 ip6table_filter,ip6_tables,ebtables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,iptable_filter,ip_tables
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
bridge                 91179  0 
stp                    12931  1 bridge
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  12 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61512  1 vfat
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
i915                  468764  3 
joydev                 17693  0 
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
iwlwifi               328352  0 
snd_seq_midi           13324  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
mac80211              506816  1 iwlwifi
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
dell_laptop            18119  0 
dell_wmi               12681  0 
dcdbas                 14490  1 dell_laptop
i2c_algo_bit           13423  1 i915
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  2 iwlwifi,mac80211
parport_pc             32866  0 
video                  19596  1 i915
psmouse                87692  0 
serio_raw              13211  0 
mei                    41616  0 
wmi                    19256  1 dell_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 

```

---

### Post by wildmanne39 on 2012-05-23
Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo ifconfig wlan0 up
```
does it connect now? this is just for testing so do not reboot if it works we will need to make it permanent.
Thanks

---

### Post by RobertSwipe on 2012-05-24
> **wildmanne39 said:**
> Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo ifconfig wlan0 up
```
does it connect now? this is just for testing so do not reboot if it works we will need to make it permanent.
Thanks

Thanks for your help.

I can't tell if it's worked, as I've already switched wifi off & on and it's currently working. (The problem seems to happen when starting from a cold boot. If I then switch wifi off/on using NetworkManager icon, it mostly works OK).

However, it is certainly **still** working, and after switching wifi off/on a few times it's worked consistently each time. Given your statement "this is just for testing so do not reboot", I'm not sure if I  should try a cold boot! Or should I just run those commands again with 11n_disable=0 to put it back to its usual state?

---

### Post by wildmanne39 on 2012-05-24
Hi, you can just reboot and the commands will be lost and if you want to test them again just run the commands again when you can not connect.
Thanks

---

### Post by RobertSwipe on 2012-05-24
> **wildmanne39 said:**
> Hi, you can just reboot and the commands will be lost and if you want to test them again just run the commands again when you can not connect.
Thanks

Thanks.

Tried a cold boot, and the problem came back. I ran your commands and everything works fine.

However, I tried another cold boot (problem came back), and this time I ran just:
 sudo ifconfig wlan0 down
 sudo ifconfig wlan0 up

...and wifi worked.

So I'm a bit lost now! It seems that simply restarting the wifi sorts out the connection problem. On first booting, the network manager icon shows I'm connected, and also identifies it as connected to my home wireless network. Why would switching the connection off then on make any difference?

I am grateful for your help.

---

### Post by wildmanne39 on 2012-05-24
Hi, let's make the change persistent and see if that fixes your issue, if not we can write another config file that should work.
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Then add one line:
```
options iwlwifi 11n_disable=1
```
save gedit,close.
Reboot
Thanks

---

### Post by RobertSwipe on 2012-05-24
> **wildmanne39 said:**
> Hi, let's make the change persistent and see if that fixes your issue, if not we can write another config file that should work.
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Then add one line:
```
options iwlwifi 11n_disable=1
```
save gedit,close.
Reboot
Thanks

Tried this and a cold reboot and..... (drum roll)....
It's worked!

Presumably this means my wifi has 802.11n disabled? Hey, if it works, I'm not too bothered - g is still operational.

Once again, thanks!

---

### Post by wildmanne39 on 2012-05-24
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by JuhazOne on 2012-05-27
> **wildmanne39 said:**
> Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo ifconfig wlan0 up
```
does it connect now? this is just for testing so do not reboot if it works we will need to make it permanent.
Thanks

Interesting. The commands ifconfig wlan0 down and ifconfig wlan0 up fixed the issue for me at least today.

It seems that my kernel didn't have the module iwlwifi loaded so it couldn't be unloaded either. I guess my corresponding kernel module would be r8169. I may try troubleshooting this again next weekend, so I'd appreciate if anyone cares to analyze the output of my computer when given wildmanne39's commands:

```
$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux myhostname 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
        Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
        Kernel driver in use: iwlagn
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
        Subsystem: Lenovo Device [17aa:21dd]
        Kernel driver in use: r8169
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 017: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 004: ID 147e:1002 Upek 
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 002 Device 003: ID 5986:03b4 Acer, Inc 
Bus 001 Device 018: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 001 Device 019: ID 0b33:0700 Contour Design, Inc. 
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"foobar"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:08:CB:CC:28   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21550  Invalid misc:483   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

$ rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
$ lsmod
Module                  Size  Used by
ipt_REDIRECT           12549  10 
xt_tcpudp              12603  10 
iptable_nat            13229  1 
nf_nat                 25890  2 ipt_REDIRECT,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  1 iptable_nat
x_tables               29846  4 ipt_REDIRECT,xt_tcpudp,iptable_nat,ip_tables
vmnet                  55617  13 
vsock                  52475  0 
vmci                   86575  1 vsock
vmmon                  80498  0 
bnep                   18436  2 
rfcomm                 47946  12 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
arc4                   12529  2 
joydev                 17693  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
thinkpad_acpi          81819  0 
nvram                  14413  1 thinkpad_acpi
tpm_tis                18546  0 
snd_hda_intel          33390  2 
snd_hda_codec         104968  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18600  1 
snd_timer              29991  2 snd_pcm,snd_seq
iwlagn                314257  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              462046  1 iwlagn
psmouse                73882  0 
serio_raw              13166  0 
cfg80211              199630  2 iwlagn,mac80211
bluetooth             166150  23 bnep,rfcomm,btusb
rts_pstor             445246  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
i915                  571299  3 
ahci                   26002  2 
libahci                26861  1 ahci
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
r8169                  52788  0 
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
video                  19597  1 i915
```

---

### Post by wildmanne39 on 2012-05-27
Hi do what is in post 13 and the 2 places that is says iwlwifi type [COLOR="Red"]iwlagn[/COLOR].
Thanks

---

### Post by JuhazOne on 2012-05-27
> **wildmanne39 said:**
> Hi do what is in post 13 and the 2 places that is says iwlwifi type [COLOR="Red"]iwlagn[/COLOR].
Thanks

Thanks for the help... But it seems that I can't even reproduce the problem right now even though I haven't touched anything under /etc/modprobe.d and I just rebooted the computer. Maybe I'll try something if the problem comes back. Anyway, thanks for your help again. :)

---

### Post by m0116815 on 2012-05-27
Hi guys,

On my end, the problem seems to have solved itself organically. Not sure why, but I'll not mess with it now :)

---

### Post by wildmanne39 on 2012-05-27
Hi, I hope it lasts but an issue not fixed usually comes back.
Thanks

---

### Post by m0116815 on 2012-05-28
Prophetic words... it has indeed come back :(

```
$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Rogue 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Dell Device [1028:04a9]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1321]
	Kernel driver in use: iwlwifi


$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor


$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Graymalkin"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:86:3B:B6:3F:E4   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.


$ rfkill list all
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by m0116815 on 2012-05-28
I was able to disable the 11n mode and now the wireless works. Interestingly, after rebooting the wireless still worked, even though the disabling did not persist. This is beginning to feel like a router issue.

---

### Post by wildmanne39 on 2012-05-28
Hi m0116815, please do:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Add one line:
```
options iwlwifi 11n_disable=1
```
Then:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by trichome tetrahydron on 2012-08-30
> **Wild Man said:**
> Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo ifconfig wlan0 up
```
does it connect now? this is just for testing so do not reboot if it works we will need to make it permanent.
Thanks
thank you so much to user RobertSwipe. I am running lubuntu 12.04 and was having the same irritating problem! I tried all manner of things, turns out it was not a problem with dns as many other threads led me to believe - your commands worked perfectly. Could you explain why they worked? what is 11n_disable=1?

---

### Post by wildmanne39 on 2012-09-01
Hi, it disables N speed because some drivers do not handle N speed well.
Thanks

---

### Post by ReetP on 2012-11-28
> **Wild Man said:**
> Hi, it disables N speed because some drivers do not handle N speed well.
Thanks

Have had the same problem with an Acer Aspire One D255 N550 using iwlwifi with a Draytek 2820 router. I guess there is a bug with the driver someplace.

The odd thing is that everything looked OK apart from the ping to a local IP address which just sits there and does nothing.

Changing the particular router to just 'b/g' and no 'n' solved it for me in the short term.

---

### Post by aldeirm2 on 2012-12-28
Hi,

I am having the same issue, i tried the last suggestion and it has improved my situation, now I can ping my router and other devices connected to the same router but still have no access to the internet or cant ping ip's outside my network.

Any one can help please?

---

