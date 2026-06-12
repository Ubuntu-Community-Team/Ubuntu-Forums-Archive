---
title: "poor wireless performance"
date: 2012-01-25
forum: General Help
---

### Post by watgrad on 2012-01-25
Hello,
I am refurbishing an old pentium 4 dual core computer to donate.  I have installed Ubuntu bit version and 11.10 and the broadcom drivers for the wireless card.  

The wireless card is working - is shows the net works around my house and lets me connect to my wireless network - showing good signal strength.  However, the quality of the connection is very poor and inconsistent.times the connection is very fast and works well.  Most of the time browsing the INTERNET or trying to update applications is so slow it is impossible...

Here is the outpu from lwconfig:
wlan0     IEEE 802.11bg  ESSID:"NoApples2"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 54:E6:FC:BF:6F:89   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr Off   Fragment thr Off
          Power Management Off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:35  Invalid misc:39   Missed beacon:0

lspci | grep Network shows this :
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Any suggestions for how to resolve this - or how to figure oout what went wrong is appreciated...

---

### Post by watgrad on 2012-01-26
Wasn't a problem with Ubuntu after all - it was a router setting, changing bandwidth from 20 to 20/40MHz solved the problem...

---

