---
title: "Compy problem- Can't find address."
date: 2011-06-27
forum: General Help
---

### Post by Milorandom123 on 2011-06-27
[I][My level of understanding of Linux is still on the low.]

[/I]
Alright so I've been messing around with Compy for a bit now, using;
-http://ubuntuforums.org/showthread.php?p=5436679
-http://ubuntuforums.org/showthread.php?p=6365702 
-http://ubuntuforums.org/showthread.php?t=281865
to set it up, and we're moving along just fine. Most problems I encounter I seem to be able to solve myself, however there's this problem with showing Internet/Networking download and upload rates. Compy reads;

"**Internet/Networking Status: (No Address)**" following with saying my down/up = 0.0 while it isn't.

This here is the little bit that should get it working;

> ${color}Internet/Networking Status: (${addr eth0})$color
Down: ${color B9D3EE}${downspeedf eth0}k/s $color${alignr}Up: ${color 26466D}${upspeedf eth0}k/s$color
${downspeedgraph eth0 25,180 000000 B9D3EE} ${alignr}${upspeedgraph eth0 
25,180 000000 26466D}Now I've already read that eth0 might be the problem, and changing it to ppp0 or ath0 might solve the problem, however it did not.

Anyone got any ideas? The core of the code is just a copy+paste from a thread so I doubt the problem is there.

---

### Post by sanderd17 on 2011-06-27
It's conky, not compy. Please edit your title or the wrong people will read this (like me).

I don't know a lot about conky though. I've just used the conky-colors script from gnome-look.org to install a basic conky.

---

### Post by Milorandom123 on 2011-06-27
Stupid mistake, thanks.

Edit: Right... change the title... obviously I can do that by clicking...
Edit: I have no idea how to edit the title of this thing.

---

### Post by marshag63 on 2011-06-27
Try using the command "ifconfig" {without quotes}in a terminal to verify if you are using eth0 or what.

With just a cursory look, aren't you missing the what color to use in the first line - it just says "color" with no specification.  You also have "downspeedf" - do you mean downspeedgraph?

MDG

---

### Post by Milorandom123 on 2011-06-27
> **marshag63 said:**
> Try using the command "ifconfig" {without quotes}in a terminal to verify if you are using eth0 or what.

With just a cursory look, aren't you missing the what color to use in the first line - it just says "color" with no specification.  You also have "downspeedf" - do you mean downspeedgraph?

MDG

Alright, I did the ifconfig part and I got;

> eth0      Link encap:Ethernet  HWaddr 6c:62:6d:69:57:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28369 (28.3 KB)  TX bytes:28369 (28.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:19:85:7c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: *xxxxxxxxxxxx* Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:780446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:681570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:799641494 (799.6 MB)  TX bytes:72084925 (72.0 MB)

I don't know why it's called wlan0 (I don't even have a lan connection), I thought I'd try changing eth0 to wlan0 and it seemed to have worked. Fully operational at the moment.

---

### Post by Wim Sturkenboom on 2011-06-27
**wireless** lan

PS you can mark your thread as solved (if it is) using the thread tools just above the first post

---

