---
title: "Ubuntu 10.04 Wireless conection"
date: 2010-05-18
forum: General Help
---

### Post by Ivan 992 on 2010-05-18
Hello I am totaly new on this forum, I am from Croatia so my english is not realy good.......
I have a problem with my ubuntu 10.04 I running it on my laptop in duall boot with windows xp professional witch is Intel Fujitsu Siemens with Atheros ar5007eg wireless card,
I have tried to conect to wlan with my card but it is disebled, I have tried so many things and dont know what to do any more, so I came here to ask experts becasuse I realy dont know what to do any more.........

This is what I got when write this in terminal

ivan@ivan-laptop:~$ **lspci | grep Network**
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

ivan@ivan-laptop:~$ **iwconfig**
lo no wireless extensions.

wlan0 IEEE 802.11bg ESSID: off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=off 
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: off

eth0 no wireless extensions.

And this.........

ivan@ivan-laptop:~$ **sudo ifconfig wlan0 up**
SIOCSIFFLAGS: Unknown error 132

I found on internet theat this error 132 is actualy a bug theat wont let my car to go up........

This whas like solution for theat bug but theat didnt help either.......

rmmod ath9k
rfkill block all
rfkill unblock all
modprobe ath9k
rfkill unblock all

So please can someone help me.........

---

