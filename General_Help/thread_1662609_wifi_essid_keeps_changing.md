---
title: "wifi essid keeps changing"
date: 2011-01-08
forum: General Help
---

### Post by zombaiooo on 2011-01-08
Hello guys,

I need help in fixing wifi on my HP tc440. I am running Ubuntu 10.04 LTS - the Lucid Lynx.

Here's the problem.

My wifi adapter is:
```

# lspci | grep Wireless
10:00.0 Network controller: Intel Corporation PRO/Wireless 2945ABG [GOLON] Network Connection (rev 02)

```
I use wicd for network manager. I can see When I try to turn on wifi, this happens:
```

# ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```
I think I found a solution for that on the Internet. This worked:
```

# rmmod iwl3945
# rfkill block all
# rfkill unblock all
# modprobe iwl3945
# ifconfig wlan0 up

```
Up to here everything worked and my adapter was running. I could see networks in the network list with wicd, but some of them had weird essids(see below). At this point I wanted to configure it for the small network that I have set up, so I did the following:
```

# ifconfig wlan0 down   // it seems this is required to set the mode
# iwconfig wlan0 mode ad-hoc
# iwconfig wlan0 channel auto
# iwconfig wlan0 essid home_tsp
# iwconfig wlan0 key 2F0AB10561

```
Now this seemed fine, because when I ran iwconfig, the output was OK:
```

# iwconfig wlan0
wlan0	IEEE 802.11abg	ESSID:"home_tsp"
	Mode:Ad-Hoc	Frequency:2.14 GHz	Cell: Not-Associated
	Tx-Power=15 dBm
	Retry long limit:7	RTS thr:off	Fragment thr:off
	Encryption key:2F0A-B105-61
	Power Management:off

```
However when it comes to setting ip address and putting the interface up, this happend:
```

# ifconfig wlan0 192.168.2.1 netmask 255.255.255.0 up
# iwconfig wlan0
wlan0	IEEE 802.11abg	ESSID:"\xF5M\xA8\x01\xBD(\x7F\x979p\xEE"\xF9V\xFF.Q\xD9H\xC28\xF7D\xA7\x1DM\x1Bz8R\x08-"
	Mode:Ad-Hoc	Frequency:2.14 GHz	Cell: Not-Associated
	Tx-Power=15 dBm
	Retry long limit:7	RTS thr:off	Fragment thr:off
	Encryption key:2F0A-B105-61
	Power Management:off

```

The essid is not only different than the one I set, but it keeps changing. This is what I got a couple of seconds later.
```

# iwconfig wlan0
wlan0	IEEE 802.11abg	ESSID:"\xDEx\x16\xAD!Q.!p-~\xA2\x9EI(`\xBBx\x8B<\x09H\x08\x9E2\x96*[\xCABF\xA9"
	Mode:Ad-Hoc	Frequency:2.14 GHz	Cell: Not-Associated
	Tx-Power=15 dBm
	Retry long limit:7	RTS thr:off	Fragment thr:off
	Encryption key:2F0A-B105-61
	Power Management:off

```
A different weird essid. It keeps and keeps changing every few couple of seconds. Even when I try to connect to a network that has a proper essid name with wcid, I can see how it is changed in the status bar of the window. I have no idea how to fix this and I didn't find any solution on the Internet. I would be very thankful to anybody who suggests something!!!

Thanks!

---

### Post by zombaiooo on 2011-01-09
Anybody? :(

---

### Post by eyalzo on 2011-03-10
It is the network-manager.
I had the same problem that was solved after I removed it from the system altogether.

---

