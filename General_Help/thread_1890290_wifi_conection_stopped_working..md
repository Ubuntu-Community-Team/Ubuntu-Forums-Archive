---
title: "wifi conection stopped working."
date: 2011-12-03
forum: General Help
---

### Post by munkefrugt on 2011-12-03
Hi.

we had 3 computers here that were going well on the wire less internet connection. but suddently the  sony vaio vgn-nr32s with ubuntu 10.04 stopped connecting to the internet. some time ago I was installing airo script on it, but I could get it to work. maybe that has something to do with it? how can I see if everything is in the right order. 
I can see the wireless network on the list of networks in the upper left coner, the network I use to go on has 3 bars out of 4
.. yes the button for the wireless is on:)

any help appreciated. thanks in advance.
-martin

---

### Post by carranty on 2011-12-03
> **munkefrugt said:**
> 
I can see the wireless network on the list of networks in the upper left coner, the network I use to go on has 3 bars out of 4

Hi, some more information would help.  What happens when you click on your network?  What error message does it give when it fails to connect?  Is this a home network? Are you sure it isn't connecting?  If you simply can't access web pages and its an office setup you could be having issues with a proxy.

Please paste the output of the command *ifconfig* to this thread.

---

### Post by munkefrugt on 2011-12-05
thanks for your fast reply. 



toor@Sony:~$ ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:1a:80:f2:b2:5f  
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
            RX packets:40 errors:0 dropped:0 overruns:0 frame:0
            TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:2960 (2.9 KB)  TX bytes:2960 (2.9 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:6a:11:79  
            inet6 addr: fe80::21f:3bff:fe6a:1179/64 Scope:Link
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:11312 (11.3 KB)
   
  toor@Sony:~$


I hope that helps:) thanks again

---

### Post by munkefrugt on 2011-12-07
Hi again. hmm. 
when I try to connect I do like I would do normaly. I press the litle icon in the upper left corner. I find my net work, which is not from an office. It then asks for a code like it use to. I press the code is already in the password plase because of the keyring.. then I press connect. no error message comes up. I see the net icon "blink" like it use to. but after a while it asks for the code again. as if it haven´t found the net. well..

Any help I apresiated:)

- martin

---

