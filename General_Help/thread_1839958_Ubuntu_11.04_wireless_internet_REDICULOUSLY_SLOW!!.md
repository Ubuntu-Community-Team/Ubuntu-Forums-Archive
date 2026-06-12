---
title: "Ubuntu 11.04 wireless internet REDICULOUSLY SLOW!!!"
date: 2011-09-06
forum: General Help
---

### Post by Bobby_Flamingo on 2011-09-06
ok i turned on my laptop today, and out of nowhere the internet is so slow it's absolutly useless, i've tried a ton of possible solutions online all day and nothing is working! i'm a complete newbie to ubuntu and any possible solutions i need to be baby stepped through, please help ubuntu is fantastic i don't want to give it up over a stupid problem.

---

### Post by pqwoerituytrueiwoq on 2011-09-06
are you sure your isp is not being a pita?
post output of [FONT=Courier New]ifconfig[/FONT] in a terminal1st we are going to try pining the modem/router to make sure the connection is not lossy
with the output of that command i can tell what address your modem/router is so it can be pinged

---

### Post by haqking on 2011-09-06
> **Bobby_Flamingo said:**
> ok i turned on my laptop today, and out of nowhere the internet is so slow it's absolutly useless, i've tried a ton of possible solutions online all day and nothing is working! i'm a complete newbie to ubuntu and any possible solutions i need to be baby stepped through, please help ubuntu is fantastic i don't want to give it up over a stupid problem.


Do you have the ability to hardwire to your router with cat5 cable ?

If so do that to make sure it is a wireless issue.

If problem still exists then it may be ISP related.

---

### Post by Bobby_Flamingo on 2011-09-06
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a8:52:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10461 (10.4 KB)  TX bytes:6172 (6.1 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:13:fa:ca  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12676 (12.6 KB)  TX bytes:16389 (16.3 KB)




that's what i got, is that what u meant??

---

### Post by Bobby_Flamingo on 2011-09-06
i already checked the wired connection and it is good

---

### Post by Bobby_Flamingo on 2011-09-06
ok it seems that after going into update manager and checking for updates, installing them and rebooting may have fixed my issue. i won't know for sure untill i wait a while and reboot to see if its permanent, because one of the other solutions temporarily worked as well

---

### Post by pqwoerituytrueiwoq on 2011-09-06
```
ping -c 15 192.168.2.1
```
post the summary at the end if you have 0% packet loss the problem is your isp or the Internet site you are connecting to

---

### Post by Bobby_Flamingo on 2011-09-06
what did you want me to do? and how can it be my isp if the wired connection is working good?

---

### Post by Bobby_Flamingo on 2011-09-06
--- 192.168.2.1 ping statistics ---
15 packets transmitted, 15 received, 0% packet loss, time 14018ms
rtt min/avg/max/mdev = 0.925/6.593/24.562/6.839 ms
 

thats what it said

---

### Post by haqking on 2011-09-06
> **Bobby_Flamingo said:**
> what did you want me to do? and how can it be my isp if the wired connection is working good?


I meant if wired connection still has same issue then it is ISP, you said it didnt so it has narrowed things down to your LAN.

your ping results look ok.


Do you have another wireless device to check the connection with ?

Have you tried power cycling your router ?

---

### Post by Bobby_Flamingo on 2011-09-06
> **haqking said:**
> I meant if wired connection still has same issue then it is ISP, you said it didnt so it has narrowed things down to your LAN.

your ping results look ok.


Do you have another wireless device to check the connection with ?

Have you tried power cycling your router ?

My ps3's wifi is still working great so i know it is the laptop

---

### Post by pqwoerituytrueiwoq on 2011-09-06
laptop distance from router
ps3 distance from router
```
ping -c 8 ubuntuforums.org
```
it could just be the site you are browsing

---

### Post by maxfire2020 on 2011-09-17
hello 

just make this file it work for me it some thing whit the usb power control 

as wlan0 is your usb wireless port 

make this file 

gedit /etc/pm/power.d/wireless

and add to it this 

> 

#!/bin/sh
/sbin/iwconfig wlan0 power off



and save 

i hope it will help you 
bye

---

