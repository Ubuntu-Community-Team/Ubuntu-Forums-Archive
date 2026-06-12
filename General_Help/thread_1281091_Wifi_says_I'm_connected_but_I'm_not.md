---
title: "Wifi says I'm connected but I'm not"
date: 2009-10-02
forum: General Help
---

### Post by xxhopingtearsxx on 2009-10-02
I have Ubuntu 9.04..

My top panel says I am connected to the internet. I go into Firefox after starting up Ubuntu, and load google. It loads. I refresh, and it attempts to load but it doesn't.. Usually, when I start Ubuntu, I would use the internet for a while.. get disconnected, wait for it to reconnect, and when it's done there's no more problems until I start Ubuntu again and it does the same thing again. Since I thought it was the usual thing, I just waited to get disconnected and connected. It happened, I went into google, but it wouldn't load.

I'm pretty frustrated, since I really don't feel like using Windows at all, but it's the only thing I can do since my wireless won't work well. What can I do? I have a realtek rtl8187b wifi and Toshiba Satellite L305-S5955.

Please respond fast. I'll take any suggestions. I really want this fixed..

I'm using an ethernet cable on Ubuntu.. had to drag it from my router, across the hallway, to here.. and now the internet is super fast like it's supposed to be. But there's a reason I got a laptop.. portability. So please help.

When I type ifconfig -a I get this:

> joey@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:cc:56:f0  
          inet6 addr: fe80::21e:33ff:fecc:56f0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2969882 (2.9 MB)  TX bytes:258841 (258.8 KB)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 6a:14:47:ad:ed:8f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:ba:99:e3  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:feba:99e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25706 (25.7 KB)  TX bytes:4722 (4.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-BA-99-E3-39-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by HappyFeet on 2009-10-02
Unplug your modem and router for 15 seconds, plug back in, and wait a couple minutes, and try it again.

---

### Post by xxhopingtearsxx on 2009-10-02
Would that really work? I don't have problems with wifi on Windows 7.

Btw, We are using WPA-PSK for our network.. I can't really change it since I don't pay for the internet, and I've heard some bad things about WPA-PSK and Ubuntu from a friend. Is that bad?

---

### Post by HappyFeet on 2009-10-02
> **xxhopingtearsxx said:**
> Would that really work?

Try it. It won't change any settings.

---

### Post by Bucky Ball on 2009-10-02
> **HappyFeet said:**
> Unplug your modem and router for 15 seconds, plug back in, and wait a couple minutes, and try it again.

Hmm. Everything else is working fine so not sure if that is going to make any difference.

Could you post the response from:

```
iwconfig
```Is the router serving an IP address (DHCP server) or you are using a static IP? Have you got matching security details and ESSID in your machine and the router? You need to get into System->Administration->Network and check.

wlan0 is what you are looking at just in case you weren't sure.

Check out the way your windows wireless connection is set up and make sure you have the same details in your Ubuntu install. Might be an idea to forget about getting on the net for the moment and just make sure you are communicating with your router and can ping it (plug a cable in and check the router config).

---

### Post by HereInOz on 2009-10-02
Open a terminal and type in:

ping 74.125.127.100

If you get a response, then you at least have a TCP/IP connection to the Internet.  If you do not get a response, then you are certainly not connected, even at the base TCP/IP level.  

If you do get a response from the above ping, type in:

ping google.com

If you do get a response from this, then you are connected and you have DNS resolution, so your browser should load web pages. If it can't, suspect a setting in the browser. 

If you get a reponse from the first ping, but not from the second, then the problem lies with DNS resolution - something like the network router/DHCP server is not correctly passing the DNS settings to your machine, or your machine is not correctly accepting them.

There are several solutions to this one, depending on how and with whom your internet connection is set up.

This is not a resolution, I understand, but at least it may lead you down the right path.

---

### Post by duckintheface on 2009-12-25
deleted

---

### Post by duckintheface on 2009-12-25
deleted

---

