---
title: "eth0 to wlan0"
date: 2012-09-07
forum: General Help
---

### Post by BStrizzy on 2012-09-07
Hey guys i'm trying to use the airodump-ng but it is saying the following, 


bstrawt@pan:~$ sudo airodump-ng mon0
Interface mon0: 
ioctl(SIOCGIFINDEX) failed: No such device


instead of me having a wlan0 it says i have a eth1 as an adapter. I am using wifi from my laptop and confused why it is saying i have eth rather than wlan. 

When i use iwconfig i get :
bstrawt@panama:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BlazinNoles"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 9*:*C:*1:*A:(:K1   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-54 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:49  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

but when i do the first code above i get that error:confused: and i also can not get it to say mon0 which i believe i should be getting?
helppp?!?!?!

---

### Post by jon zendatta on 2012-09-07
It depends what wireless driver you're using. To place my card in monitor mode ->
```
sudo airmon-ng start wlan0
```

```
Interface	Chipset		Driver

wlan0		Atheros AR9280	ath9k - [phy0]
				(monitor mode enabled on mon0)
```

---

### Post by BStrizzy on 2012-09-07
> **jon zendatta said:**
> It depends what wireless driver you're using. To place my card in monitor mode ->
```
sudo airmon-ng start wlan0
``````
Interface    Chipset        Driver

wlan0        Atheros AR9280    ath9k - [phy0]
                (monitor mode enabled on mon0)
```


is there a way i can pick a wireless driver? I just need to get mon0 for airodump. everytime i do 

bstrawt@pa**a:~$ sudo airmon-ng

Interface    Chipset        Driver

wlan0        Unknown         wl


^ WHYYYYYYYYYYYY^  its like it can not reconize my wifi card or something

---

### Post by jon zendatta on 2012-09-07
No you do not have a choice of drivers. Check your driver is compatible, not all facilitate monitor mode.
[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers")

---

### Post by BStrizzy on 2012-09-07
> **jon zendatta said:**
> No you do not have a choice of drivers. Check your driver is compatible, not all facilitate monitor mode.
[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)


you gotta be kidding me, i dont think i see it in the list. there has to be a way!

---

