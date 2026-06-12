---
title: "Slow wirless conection Ubuntu 11.10"
date: 2012-02-14
forum: General Help
---

### Post by eduloni on 2012-02-14
hello. my conection is very slow im a new ubuntu user.
im using ubuntu 11.10 on a toshiba satellite l645-s4056

lspci -nn | grep 0280:
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"belkin.31d2"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 94:44:52:C5:C1:D2   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1297   Missed beacon:0
```

---

### Post by chili555 on 2012-02-14
So, far, things look quite good. Please let's see:```
ping -c3 www.google.com
lsmod | grep 819
```Thanks.

---

### Post by eduloni on 2012-02-15
ping c-3 [www.google.com:](www.google.com:)
```
PING www.l.google.com (74.125.113.147) 56(84) bytes of data.
64 bytes from vw-in-f147.1e100.net (74.125.113.147): icmp_req=1 ttl=48 time=105 ms
64 bytes from vw-in-f147.1e100.net (74.125.113.147): icmp_req=2 ttl=48 time=111 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2002ms
rtt min/avg/max/mdev = 105.885/108.870/111.856/3.003 ms

```


lsmod | grep 819:
```
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
mac80211              462046  3 rtl8192ce,rtl8192c_common,rtlwifi

```

---

### Post by chili555 on 2012-02-15
That is a bit liesurely and I see you have a dropped packet. Let's dig deeper:```
ping -c3 8.8.8.8
cat /etc/resolv.conf
sudo cat /var/log/syslog | grep wlan | tail -n20
```You don't appear to have any conflicting drivers loading. Thanks.

---

### Post by eduloni on 2012-02-15
hello
this morning my wireless seems to be working just fine. 
Thank you for your help

---

