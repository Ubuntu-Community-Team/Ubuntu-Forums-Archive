---
title: "wireless connecting only when wired!!"
date: 2011-02-13
forum: General Help
---

### Post by rajn on 2011-02-13
Hi Wireless experts,
I am going crazy setting up my wireless and I had thought I had set up everything till I took my computer of the wired internet to another room to find out my wireless does not work.

I did many things like change from WAP to WEP
installed wicd.

However, now my network manager (old) recognizes the wireless and I can set it up. It says connected also finds the wireless but I cannot browse.
Wicd only sees the wired but only sometimes sees the wireless. But when I try to connect with WEP/WAP and all other combinations it always gives me password incorrect error.

I do not understand what is happening
ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:2a:43:9c  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe2a:439c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8360006 (8.3 MB)  TX bytes:1432305 (1.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19848 (19.8 KB)  TX bytes:19848 (19.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:76:10:b8  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe76:10b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:33963 (33.9 KB)

I then disconnect not physically by removing the wire but by going to wicd and then I cannot browse. Moreover, in that case the output of ifconfig is

eth0      Link encap:Ethernet  HWaddr 08:00:46:2a:43:9c  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe2a:439c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8359722 (8.3 MB)  TX bytes:1431879 (1.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18664 (18.6 KB)  TX bytes:18664 (18.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:76:10:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:28224 (28.2 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:1f:76:10:b8  
          inet addr:169.254.6.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

I am not sure why I am getting teh avahi link and moreover I do not see anymore the inet address on wlan0

ifconfig ifup wlan0 does not recognize the command

iwconfig gives
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HisMES-Wireless"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 92:D8:06:23:FE:D4   
          Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


I really do not know what to display of dmesg because it is too long and I do not know what is relevant. But here are the last few lines from
dmesg

[ 1599.002139] wlan0: Creating new IBSS network, BSSID d6:9d:b3:c9:2b:d3
[ 1629.002110] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1689.002102] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1727.587676] wlan0: Trigger new scan to find an IBSS to join
[ 1730.002309] wlan0: Trigger new scan to find an IBSS to join
[ 1734.001627] wlan0: Trigger new scan to find an IBSS to join
[ 1736.001324] wlan0: Creating new IBSS network, BSSID a2:09:41:e9:1f:ba
[ 1738.444083] wlan0: no IPv6 routers present
[ 1746.761131] wlan0: Selected IBSS BSSID a2:09:41:e9:1f:ba based on configured SSID
[ 1780.001940] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 1813.109404] wlan0: Trigger new scan to find an IBSS to join
[ 1813.857847] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1813.860231] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 1813.860660] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1815.342075] wlan0: Trigger new scan to find an IBSS to join
[ 1818.001612] wlan0: Trigger new scan to find an IBSS to join
[ 1819.549581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1824.268090] eth0: no IPv6 routers present
[ 1858.457093] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1859.553480] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1859.556235] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 1859.558921] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1869.564107] eth0: no IPv6 routers present
[ 2061.492283] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2062.836997] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2063.646624] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2063.648226] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2063.648641] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2065.238572] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2073.924062] eth0: no IPv6 routers present
[ 2106.404414] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2107.217850] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2107.220223] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2107.221640] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2117.340078] eth0: no IPv6 routers present
[ 2221.011137] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2244.081311] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2244.633862] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2244.636241] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2244.636674] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2245.151142] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2245.152217] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2245.153099] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2247.339192] type=1503 audit(1297634793.994:22):  operation="open" pid=4104 parent=4088 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[ 2249.512483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2249.845890] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2249.848248] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2249.849054] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2255.990799] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2256.270018] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2256.272233] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2256.273429] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2267.156048] eth0: no IPv6 routers present
[ 2347.634031] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2348.229872] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2348.232299] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2348.232969] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2358.724088] eth0: no IPv6 routers present
[ 2907.214442] wlan0: Trigger new scan to find an IBSS to join
[ 2910.002595] wlan0: Trigger new scan to find an IBSS to join
[ 2914.001889] wlan0: Trigger new scan to find an IBSS to join
[ 2916.002580] wlan0: Creating new IBSS network, BSSID 92:d8:06:23:fe:d4
[ 2918.140051] wlan0: no IPv6 routers present
[ 2946.000427] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3006.002556] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3066.001546] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3126.002546] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3186.001632] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3246.002540] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)

Any help is appreciated.
I tested with edimax and also with Linksys WUSBG54 but both behave the same way. I do see network on lwscan but with wired connection removed I cannot browse. Server not found is the output.
And I am not in the "Work offline" mode

---

