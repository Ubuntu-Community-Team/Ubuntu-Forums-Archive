---
title: "Wireless network not detected 10.04"
date: 2010-09-14
forum: General Help
---

### Post by micha8l on 2010-09-14
Hello, I'm having a problem detecting my wireless network. My laptop detects my neighbours networks, but not my own. 

I'm using a fresh copy of 10.04 and when I first started the computer my wireless network was detected and even worked! But now, it's just vanished... All I've done to the computer is used two commands:

```

sudo apt-get update

``````

sudo apt-get upgrade

```When I run iwconfig it prints:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```Kind regards
Mike

---

### Post by micha8l on 2010-09-14
bump

I've still found no solution. About an hour ago Ubuntu detected my network, out of the blue, and not it has vanished again -- it seems like a fault :/

---

### Post by pcdave98 on 2010-09-14
If you know your SSID and password try adding the connection manually.

---

