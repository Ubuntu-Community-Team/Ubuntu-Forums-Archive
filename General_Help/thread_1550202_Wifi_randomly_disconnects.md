---
title: "Wifi randomly disconnects"
date: 2010-08-10
forum: General Help
---

### Post by redfox1160 on 2010-08-10
I don;t know what is wrong, but my wifi connection randomly disconnects. This has happened ever since I installed 10.04 (months ago), I just never thought to fix it. It does not last long, only like 10 seconds, and then it reconnects. Here is the output from ifconfig and iwconfig:
```
eric@grossboys-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:3e:68:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29656 (29.6 KB)  TX bytes:29656 (29.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:73:97:db  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe73:97db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:39610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51898959 (51.8 MB)  TX bytes:3215682 (3.2 MB)

eric@grossboys-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Gross"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:75:19:0D:9A   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
```

---

### Post by redfox1160 on 2010-08-10
Does anyone know what I can do? Should I reinstall my wifi drivers?

---

### Post by claracc on 2010-08-11
Have you tried wicd (in repositories) instead of gnome network manager to control wifi?

---

### Post by redfox1160 on 2010-08-11
No, ill have to try that. Will it work the same way that gnome network manager works?

---

### Post by claracc on 2010-08-11
Yes, for me works better because since I installed karmic koala I had to use wicd to manage wifi (Intel Corporation PRO/Wireless 3945ABG) since gnome network manager continuously connecting and disconnecting the net.

In karmic koala, if you select in synaptic wicd to install, it automatically uninstalls gnome network manager and installs wicd.

I expect it can help.

---

### Post by redfox1160 on 2010-08-12
I installed it, and it is working right now. Should I uninstall the gnome network manager? Thanks!

---

### Post by claracc on 2010-08-12
Yes, I would uninstall network-manager and network-manager gnome.

---

### Post by redfox1160 on 2010-08-13
I am still having the problem.

---

### Post by claracc on 2010-08-14
Perhaps changing your router's channel in the configuration page of the device fixes the problem.
 
I had to change mine from 11 to 6.

---

