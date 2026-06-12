---
title: "Syslog: wpa_supplicant every 2 minutes"
date: 2009-11-01
forum: General Help
---

### Post by edantes on 2009-11-01
I just installed 9.10 from scratch in a system using a wifi adaptor Atheros AR5001X+ (AR2414 chipset).  Ubuntu 9.10 automatically assigns to it the ath5k driver.  With 9.04 this combination was problematic resulting in frequent crashes solved when I switched to the madwifi driver.  Madwifi is not available with 9.10.

I had one unexplained crash in the 48 hours I've been running 9.10.  Examining the syslog, I noticed a message from wpa_supplicant every 2 minutes.  Other than that one crash, the system seems to be running fine. 

Is the wpa_supplicant insistence a problem in itself?  A bug?

Here is a sample from syslog:

-----
Nov  1 12:48:37 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 12:50:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 12:52:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 12:54:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 12:56:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 12:58:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 13:00:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 13:02:37 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 13:04:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS

---

### Post by anti-destin on 2009-12-02
i'm getting this problem, too. the constant logging causes the log files to grow rather quickly.

i'm running 64-bit ubuntu 9.10 (minimal installation) with kde-minimal on top. i also have an atheros wireless card.

---

### Post by Steenmeijer on 2009-12-03
Add another one to the list, except in my case it does more than make a log file entry; every time this happens my network connection is frozen for about 1 second. I noticed first because I was using synergy and when I looked through the logs for something else the timing looked very suspicious.

---

### Post by Steenmeijer on 2009-12-03
Ok so I "fixed" the problem by switching from network manager to wicd, it's very easy:

sudo apt-get install wicd

The GUI wil be in the programs menu, by adding wicd-client to your startup list you get the tray-icon.

---

### Post by bbear1 on 2010-03-08
Steenmeijer,
I can't tell you how thrilled I was to read your post. I have been struggling to fix the network drop problems with my Linksys WUSB600N V2 for months now!

I can't believe that the solution turned out to be something as simple as switching to using wicd

I still see the rt_ioctl_giwscan messages in the log files but the network connection itself appears to be rock solid now :D

thanks so much for your help.

---

### Post by Wulfrunner on 2010-06-03
Read more about this bug and how to fix it here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680)

---

