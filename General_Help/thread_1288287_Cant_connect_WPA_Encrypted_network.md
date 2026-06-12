---
title: "Cant connect WPA Encrypted network"
date: 2009-10-11
forum: General Help
---

### Post by simartem on 2009-10-11
I have got a USB Wireless device with RTL8187 chipset. It was working fine until i installed a new driver, the new driver is to be used with Aircrack. Somehow, i dont seem to connect to my own home wireless connection which is in WPA Encryption. To sum up,  i cant connect encrypted networks. I have heard about "WPA SUPPLICANT" but i dont know how to setup or install this. Can somebody please help ?

---

### Post by Peter09 on 2009-10-11
Can you post the output of the command

```
ifconfig
```

---

### Post by simartem on 2009-10-11
ifconfig result :

```


eth0      Link encap:Ethernet  HWaddr 00:0c:6e:d0:1e:94  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fed0:1e94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1688 errors:0 dropped:0 overruns:1 frame:0
          TX packets:1241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1407270 (1.4 MB)  TX bytes:207010 (207.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6064 (6.0 KB)  TX bytes:6064 (6.0 KB)

wlan1     Link encap:Ethernet  HWaddr 00:e0:4c:83:05:81  
          inet6 addr: fe80::2e0:4cff:fe83:581/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:366 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:452 (452.0 B)  TX bytes:1052 (1.0 KB)


```

---

### Post by simartem on 2009-10-11
bump

---

### Post by B!aine on 2009-10-11
I installed Wicd network manager to be able to connect to wpa encrypted networks.  For me using 9.04, the default network manager would connect to unencrypted networks, but not wpa encripted ones.  Installing wicd automatically un-installed the default network manager so there is not two managers.  You can get it from add/remove applications or by pasting ```
sudo apt-get install wicd
``` into a terminal window.  Then just configure it and you hopefully will be set.

---

### Post by simartem on 2009-10-21
Thank you B!aine.. I will give it a try but how can i uninstall the default network manager ?

---

### Post by ColdFFF on 2009-10-21
> **simartem said:**
> how can i uninstall the default network manager ?

> **B!aine said:**
> Installing wicd automatically un-installed the default network manager so there is not two managers.


I would actually recommend keeping network manager on your system by using apt-get, but not installing it just incase you cant get wicd working and need to reconnect to the internet (you dont want to be stuck with a totally non-functional network manager)

---

