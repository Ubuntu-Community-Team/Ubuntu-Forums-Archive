---
title: "NO Internet access ...please help..."
date: 2011-07-27
forum: General Help
---

### Post by zombieub on 2011-07-27
NO Internet access ...please help...

hi ...i am totally new to linux and i love the concept...but the problem i am facing is i am not able to access my internet through ubuntu 11.04. DESKTOP
..i have dual boot windows 7 + ubuntu 11.04...
all i kknow and could know by googling is to run command in terminal....
Pasting the results ....

**sudo pppoeconf**

Sorry, I scanned 1 interface, but the Access &#9474;
&#9474; Concentrator of your provider did not respond. Please &#9474;
&#9474; check your network and modem cables. Another reason for &#9474;
&#9474; the scan failure may also be another running pppoe &#9474;
&#9474; process which controls the modem


**ifconfig**

eth0 Link encap:Ethernet HWaddr 00:25:64:72:2e:72
inet6 addr: fe80::225:64ff:fe72:2e72/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:720 (720.0 B) TX bytes:4222 (4.2 KB)
Interrupt:18

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:960 (960.0 B) TX bytes:960 (960.0 B)


wat am i doing wrong.....wat am i supposed to do....please help

i have cable + router....however m trying to work it up with cable net first coz i guess my driver for wireless connectivity in ubuntu is missing.....


how do i connect.....here it is....

Cable > into the laptop slot > open web browser > ISP opens a page by itself, asks for username and password > log in > internet is ready to use.....

wirelss > open web browser > ISP opens a page by itself, asks for username and password > log in > internet is ready to use....

---

### Post by seawolf167 on 2011-07-27
Just need some clarification - when you physically plug an ethernet cable into the port on your laptop and the other end into your gateway are you able to access the internet?

The username/password login - is this to access a network you have setup?

---

### Post by zombieub on 2011-07-27
in windows 7 yes i am able to access when i plug in cable in my laptop.....
but in ubuntu NO i am not able to...

and about the username/password.....as soon as i plug in my cable/wifi widows prompt....addtional information may be required to access internet...then i open browser(mozilla) and the first page i see is ISP page.....which asks for username and password....and as soon as i enter the detail.....i am connected to internet...

---

### Post by seawolf167 on 2011-07-27
> **zombieub said:**
> and as soon as i enter the detail.....i am connected to internet...

So you can get internet once you enter your credentials?

You can see if you have any available wireless drivers once you are connected by checking under Additional Drivers,  System -> Administration -> Hardware Drivers or in 11.04, click the power button in the upper-right, select System Settings, then select Additional Drivers.

---

### Post by zombieub on 2011-07-27
additional driver for wirless is missing...and in order to install that i need internet connectivity...which i am not able to do thru cable...

---

