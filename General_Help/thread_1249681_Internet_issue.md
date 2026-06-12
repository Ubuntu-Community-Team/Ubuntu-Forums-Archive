---
title: "Internet issue"
date: 2009-08-25
forum: General Help
---

### Post by ECoder on 2009-08-25
Hello,

Yesterday I installed Ubuntu 9.04. Everything went fine, today I installed apache2, php5, libapache2-mod-php5 and now I'm experiencing some internet problems. I need to reset my modem before I have access to Internet on Ubuntu. I got internet if I restart into Windows XP, next I booted up in Ubuntu and the NetWork Manager says everything is fine, I've got a wired connection but no Internet. If I try to ping google.com I get:

Could not reach network

I'm not sure it has something to do with apache, I have absolutely no clue. I'm sure it is something with Ubuntu, no problems at all in Windows.

Thanks!

Peter

---

### Post by tgeer43 on 2009-08-25
This doesn't really get to the root of the problem but may be an acceptable workaround. You could try initializing your connection by adding the following lines in /etc/rc.local:
```
ifconfig eth0 up
iwconfig eth0 mode managed
iwconfig eth0 essid *YOUR_ESSID* 
iwconfig eth0 key open *YOUR_WEP_KEY*
dhcpcd -d eth0
```Assuming that your wired connection is called eth0 and you replace the values above with your correct Essid and Wep key.

Might as well try it. It takes only a minute and is easily reversible if it doesn't help. 

Additionally, you could try removing the Apache packages that you installed to see if the problem clears up. Then you would at least know if they are related to the issue.

tgeer

---

### Post by louieb on 2009-08-25
Please post the output of ```
ifconfig
```

Try to use DHCP to get an IP address  (post output)
```
sudo dhclient
``` 

Wired connections usually just work  Have not seen installing  LAMP interfere with getting an Internet connection.

---

### Post by ECoder on 2009-08-26
Thanks for the help,

I figured something out. When I start Ubuntu, I've got no internet. When I run the dhcpcd command I get a new IP adress and then everything is fine!

```

eth0      Link encap:Ethernet  HWaddr 00:16:17:74:86:50  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe74:8650/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2677 (2.6 KB)  TX bytes:5327 (5.3 KB)
          Interrupt:250 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

peter@peter-desktop:~$ sudo dhcpcd eth0
[sudo] password for peter:
peter@peter-desktop:~$ dhcpcd.sh: interface eth0 has been configured with new IP=192.168.1.67

peter@peter-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:74:86:50  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe74:8650/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2677 (2.6 KB)  TX bytes:5327 (5.3 KB)
          Interrupt:250 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

I've got internet, but how can I fix this so that the right IP adress will be automatically configured when I boot in Ubuntu? 

Thanks!

---

