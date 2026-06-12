---
title: "login problem on certain websites"
date: 2011-04-15
forum: General Help
---

### Post by saedz on 2011-04-15
Hellooooooo,
 
I am a newbie to Linux, and so glad to be here
I used to run fedora on my Dell Inspiron 6400 for a month, but there was a funny problem on web browsing(and thunderbird smtp when sending mails), so I decided to run Ubuntu to check if the problem persist or not.
 
Unfortunately YES
 
here it is:
I can login to gmail (and all other google services), facebook, hotmail. yahoo etc only once then I'm not gonna be able to open the specified website again and navigate to other pages, NOTHING comes up in firefox 3.6 and 4, chrome, opera etc.
but if I clear browser's cache and cookies then I can login again another time,but the same problem happens.
 
A complete fresh Ubuntu 10.10 is installed on my laptop including all latest updates
-I have disabled SELinux and Firewall.
-Reseted the ADSL DLink router to factory default (firewall is disabled).
-Either wireless or wired connections had the same issue.
-IPv6 is disabled
-"network.dns.disableIPv6" is true in firefox
-A vitrualbox windows XP machine also couldn't solve the problem
 
ifconfig:
eth0 Link encap:Ethernet HWaddr 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:70 errors:0 dropped:0 overruns:0 frame:0
TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5164 (5.1 KB) TX bytes:5164 (5.1 KB)
wlan0 Link encap:Ethernet HWaddr 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:934 errors:0 dropped:0 overruns:0 frame:0
TX packets:1005 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:537632 (537.6 KB) TX bytes:207915 (207.9 KB)
 
Whilst I have no problem on a computer connected to the same ADSL Router with MS windows
p.s. I couldn't even create an account for ubuntuforums.org (timeouts returned) as well as submitting this thread(I used the other computer)
 
Many thanks in advanced.
Regard,
saed

---

### Post by Dave_L on 2011-04-15
I assume your firefox settings are not restricting cookies or Javascript?

I've found this add-on useful in diagnosing some problems:

[https://addons.mozilla.org/en-us/firefox/addon/live-http-headers/](https://addons.mozilla.org/en-us/firefox/addon/live-http-headers/)

In this case, you could use the add-on on a working computer and a non-working one, and see if there are any differences in the sent or received headers.

---

### Post by saedz on 2011-04-16
Probably the JavaScript and Cookies are enabled.

I checked both systems with the plug-in(thanks,very interesting utility), when logging into gmail nothing happens in live HTTP header, captured files are attached.
 
But I think this has nothing to do with browser's configuration as I am having the same problem in virtual machine installed (bridged or NAT) 
 
I believe some network configuration must be manipulated but I don't know what and which one.

---

### Post by saedz on 2011-04-17
I think when the problem is happening in both Fedora and Ubuntu, a driver or network component is causing the issue
 
mostly on HTTPS, SSL pages and when submitting forms

---

