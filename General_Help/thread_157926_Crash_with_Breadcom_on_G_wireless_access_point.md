---
title: "Crash with Breadcom on G wireless access point"
date: 2006-04-10
forum: General Help
---

### Post by Varoudis on 2006-04-10
Hello,
I have an Acer Ferrari 4005 laptop and everything was OK until I switch my old Cisco AP350 (801.11b) access point with a USR 9108 MAXg (b/g) wifi adsl router.

When I try to use the network applet from gnome the system crash (total crash)  to change ESSID (the essid is the same but it need to get the new MAC addr) and activate.

Before that the wifi use active on boot with no problem.
I tried to make it work in B mode (iwpriv wlan0 network_mode b) and by hand
ifconfig wlan0 down
iwconfig wlan0 essid any 
(iwconfig now shows that everything is OK in both B or 54G mode)
and when I do ifconfig wlan0 up tha system crashes (I dont even get the shell prompt back)

root@SiaMal:~# lsmod |grep  ndis
ndiswrapper           148692  0

0000:05:00.0 Ethernet controller: Broadcom Corporation: Unknown device 169d (rev 11)
0000:06:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

root@SiaMal:~# ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

root@SiaMal:~# uname -a
Linux SiaMal 2.6.12-10-amd64-generic #1 Sat Mar 11 16:15:30 UTC 2006 x86_64 GNU/Linux

Is this driver working only with B access point? Anyone to have use something like this?

Thnx,
Tasos Varoudis

---

