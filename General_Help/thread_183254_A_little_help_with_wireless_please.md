---
title: "A little help with wireless please"
date: 2006-05-27
forum: General Help
---

### Post by steveland? on 2006-05-27
Hi folks,
Just installed Ubuntu on my Advent 7027 laptop.

It has a built in Intel® PRO/Wireless 2100 Network Connection card using the Broadcom BCM4301 chipset.

Now apparently this chipset doesn't have Linux drivers (well, according to the fact that there's a petition for the drivers and all floating around...) but the laptop picks up the wlan0 connection and when I try to configure the wlan it finds the SSID of my network so I know it's picking up something...

I've configured it to activate the wlan, put in my WEP Key, enabled DHCP and saved all the settings using the Networks option in the System>Administration menu.

I can't get online with it at all

For a little while I could ping 192.168.1.1 (Linksys WAG54G router, set to Mixed mode with WEP enabled) but no longer, just tells me the network is unreachable at the moment...

Running ifconfig gives me the following output:

```
eth0    Link encap:Ethernet  HWaddr 00:03:0D:02:85:E1
        inet6 addr: fe80::203:dff:fe02:85e1/64 Scope:Link
        UP BROADCAST MULTICAST   MTU:1500   Metric:1
        RX Packets:0  errors:0  dropped:0  overruns:0 frame:0 
        TX Packets:0  errors:0  dropped:0  overruns:0 carrier:0
        collisions:0 txqeuelen:1000
        RX bytes:0 (0.0b)  TX bytes:0 (0.0b)
        Interrupt:10 Base address:0Xcc00

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING   MTU:16436   Metric:1
        RX Packets:5934  errors:0  dropped:0  overruns:0 frame:0 
        TX Packets:5934  errors:0  dropped:0  overruns:0 carrier:0
        collisions:0 txqeuelen:0
        RX bytes:537448 (524.8 KiB)  TX bytes:537448 (524.8 KiB)

wlan0   Link encap:Ethernet  HWaddr 00:90:4B:2E:1D:A5
        inet6 addr: fe80::290:4bff:fe2e:ida5/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
        RX Packets:0  errors:0  dropped:0  overruns:0 frame:0 
        TX Packets:0  errors:0  dropped:0  overruns:0 carrier:0
        collisions:0 txqeuelen:1000
        RX bytes:0 (0.0b)  TX bytes:0 (0.0b)
        Memory:dbff8000-dbff9fff
```

iwconfig wlan0 gives:
```

IEEE 802.11b  ESSID:off/any
Mode:Managed  Frequescy:2.437 GHz  Access Point: 00:00:00:00:00:00
Bit Rate:11 Mb/s   Tx-Power:16 dBm
RTS thr:2347 B   Fragment thr:2346 B
Power Management:off
Link Quality:100/100  Signal Level:-10 dBm  Noise level:-256 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:24   Missed beacon:0
```

Anyone have any ideas?

---

### Post by oscar on 2006-05-27
It looks like you aren't getting an ip address from your router, what happens when you go:
```
sudo dhclient wlan0
```
Your chipset does have drivers, the intel wireless chipsets are among the best supported.

---

### Post by steveland? on 2006-05-27
OK I've upgraded to Dapper and installed network-manager

wlan0 is now eht1.

I've tried using nm-applet to configure the connection.

Should I just put in the SSID of the network I use or is there a way of scanning for a wireless network in the vicinity?

the output for sudo dhclient eth1 is:
```
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:90:4b:2e:1d:a5
Sending on  LPF/eth1/00:90:4b:2e:1d:a5
Sending on  Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
```
At that point I ctrl-c'ed to cancel it.

The new output of iwconfig eth1 is:
```
IEEE 802.11b  ESSID:"<MY SSID>"  Nickname:"Broadcom 4301"
Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
RTS thr:off   Fragment thr:off
Link Quality:0  Signal Level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:24   Missed beacon:0
```

Still can't connect to the wireless network. It searches for a while but then can't connect

---

### Post by steveland? on 2006-05-28
Sorry for bumping this thread, they just slip down the pile so quickly :(

Can anyone help me?

---

### Post by Titus A Duxass on 2006-05-28
Try disabling your eth0 network card in BIOS.
Then restart, eth1 should become wlan0.

If you still have no joy, shutdown but don't remove power, remove the wireless card, reboot, shutdown but don't remove power, replace wireless card and then reboot.

---

### Post by steveland? on 2006-05-28
Thanks I'll try disabling eth0 but I won't be able to take out the wireless card as it's internal :(

---

### Post by Scorpuk on 2006-05-28
Most laptops come with a switch to turn the internal wireless cards on or off. Just press that and it should be as though you remved it.

---

