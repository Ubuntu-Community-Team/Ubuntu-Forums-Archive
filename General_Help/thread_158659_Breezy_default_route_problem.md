---
title: "Breezy default route problem"
date: 2006-04-11
forum: General Help
---

### Post by rabidphage on 2006-04-11
While installing breezy, the wireless network that i'm in is properly detected and configured via dhcp. However i get a prompt suggesting that the default route is not configured and asks me to assign an ip for it. After continuing the installation leaving this field blank and booting in to the desktop, the wifi network appears connected but i cannot access the internet. The DNS tab on the network manger doesn't show any entries. 
What is going on???
please help...](*,)

---

### Post by rabidphage on 2006-04-11
somebody help pleaseeeeee

---

### Post by OfficeLinebacker on 2006-04-11
Can you please restate your problem?

---

### Post by dcstar on 2006-04-11
[QUOTE=rabidphage]While installing breezy, the wireless network that i'm in is properly detected and configured via dhcp. However i get a prompt suggesting that the default route is not configured and asks me to assign an ip for it. After continuing the installation leaving this field blank and booting in to the desktop, the wifi network appears connected but i cannot access the internet. The DNS tab on the network manger doesn't show any entries. 
What is going on???
please help...](*,)[/QUOTE]
Post the output of the following:
```
netstat -r
ifconfig
iwconfig
```

---

### Post by rabidphage on 2006-04-12
Thanks guys,,
I moved on. I've got Dapper Drake flight 6 installed and the problem seems solved for now.

---

### Post by rabidphage on 2006-04-13
Dapper connects whenever it feels like.Haven't got a clue whats goin on


darx@darx:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.25.26.0     *               255.255.255.0   U         0 0          0 eth0


darx@darx:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"wolfradiolan"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:0D:65:48:79:65
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=-57 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

darx@darx:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.25.26.0     *               255.255.255.0   U         0 0          0 eth0

---

### Post by cronholio on 2006-04-13
Whenever it doesn't work, you can do:

```
sudo dhclient eth0
```

It should help.

---

### Post by rabidphage on 2006-04-13
This is what I get

darx@darx:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:ce:3c:ce:3c
Sending on   LPF/eth0/00:13:ce:3c:ce:3c
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.25.24.1
SIOCADDRT: Network is unreachable
bound to 172.25.27.192 -- renewal in 1537 seconds.

Still no connection
](*,)

---

### Post by rabidphage on 2006-04-13
When i installed dapper I entered the wireless connection as the default
I got it working apparently by dropping eth1 which is obviously the lan
```
sudo ifconfig eth1 drop
sudo invoke-rc.d networking restart
sudo dhclient eth0
```
maybe its a random succes.. will have to wait untill the next reboot.

---

