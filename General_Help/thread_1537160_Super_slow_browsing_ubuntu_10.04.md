---
title: "Super slow browsing ubuntu 10.04"
date: 2010-07-23
forum: General Help
---

### Post by tataraperz on 2010-07-23
Hi, new to the forums and new to ubuntu, set up everything flawlessly and was ready to dump windows. "Not so fast my friend!"-Ubuntu yelled.

Straight to the point, web browsing is going SUPER slow in my samsung N150 netbook with dual boot(win7/ubuntu10.04). Windows counterpart working flawlessly.

Into the details:

The problem is, i go into a website and it seems to renderize by chunks, ie i enter my favorite PC hardware forum and it is like this when loading: Processors...1sec....Vid cards....1sec...Memory...and on and on until the bottom of the page is reached. The normal behavior is: Click...forum loaded ,as on windows.

By default i use my wireless conection, but also tried wired one to no avail. Also tried it from the live cd and i have the same problem. Some sitess like google, gmail and youtube load normally(instantly). I've tried disabling ipv6 as adviced in several parts and had no results. I used the default firefox 3.6.6, firefox 3.6.7 and chrome with the same results.

This is the info for my wireless adapter just in case:

description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: f0:7b:cb:0d:d9:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0100000-f010ffff

Thanks fellas!

---

### Post by mdramige on 2010-07-23
When you tried the wired connection did you disable wireless? I just want to make sure the wireless is isolated as the cause of your problem before proceeding.

---

### Post by tataraperz on 2010-07-23
Yes, disables wireless adapter then plugged into ethernet

---

### Post by FahadMKS on 2010-07-23
This issue is mainly due to the Unwated temp files on the computer.

The wireless connection will be slow as compared to the Wired one, so you can try to remove all the unwanted temp files on the computer.

if you are not aware on how to do that, you may make use of the software the Bleachbit on the ubuntu Software center.

if you have any doubts, you may please do reply.

---

### Post by tataraperz on 2010-07-23
I used bleachbit and selected almost every option with gksu and gained some nice space, sad enough my intial problem persists :I

---

### Post by cloyd on 2010-07-23
What browser are you using? With Firefox, I sometimes have problems when signal strength is under 40%.  Chrome often works better. I like Firefox better when it works. Also, I have the 2.6.36 kernel. It seems to handle my wireless better than some others. Also, getting kernel backports for wireless in synaptic is helpful.


Edit: I have a 2.6.34 kernel. It also runs a little cooler than 2.6.32.

---

### Post by tataraperz on 2010-07-29
*Well, after trying a lot of stuff, installing and resinstalling ubuntu 10.04, UNR 10.04, kubuntu 10.04, xubuntu 10.04 and ubuntu 8.04, browsing the internet is still painfully slow.

I've tried this to no avail:

- Disabling IPv6 in firefox and in the whole system.
- Using OpenDNS.
- Setting up static IP.
- Using wired instead of wireless.
- Installing backported drivers.
- Removing the router and plugging directly to my cablemodem.
- Changing MTU.
- Updating kernel to most recent.
- All combinations of the points mentioned before.

I simply can't imagine what is going wrong. I've tried installing in my desktop, netbook, laptop all with the same problem no matter what. Using windows on any of those computers everything is blazing fast.

Speed when sharing files in my local network is top notch.

This behaviour is rather erratic and unpredictable but happens like 75% of the time. For example, everytime i try to enter [http://www.bleachcentral.com](http://www.bleachcentral.com) it loads a part of the page and sits there like for 5 minutes contacting d.pubgears.com and then loads. Another example: [http://foro.noticias3d.com](http://foro.noticias3d.com) sometimes works flawlessly
*for 3 or 4 clicks then it is slow as hell, like: Processors...3sec...Vid cards... and so on.

Some sites like google ones(gmail, youtube, etc), facebook(have problems to comments, view all comments, view online friends) and some others work if anything, a bit slower than in windows. 

Help pls!!

---

### Post by tataraperz on 2010-07-29
bummp

---

### Post by landersohn on 2010-09-14
Can't give you much help but I do experience the exact same problem: behind the router speed is great, anything that goes out has sporadic nature: it connects for a few seconds then it sits for minutes.

---

### Post by kopiluac on 2011-05-18
I also  have this issue. Just started this week and I have no clue as to why. Connection is fast 10meg. But browsing with FF is super slow. Sometimes it takes over a minute to load a page. The issue seems to be Ubuntu intensive. (I have Ubuntu 10.4 on my laptop and 10.10 on my desktop with a dualboot partition for Windows 7. Like the original poster articulated earlier, my Ubuntu installs are browsing at a snail's pace. However, my Windows 7 partition (also with FF) is smokin fast. Browsing was never an issue in my FF before on ubuntu once I made the Ubuntu specific tweaks to FF. I run 4.0 on my desktop and 3.0 on my laptop. The behavior is identical. Any help would be greatly appreciated. 

Thanks

---

