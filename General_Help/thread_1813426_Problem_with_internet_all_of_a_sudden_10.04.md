---
title: "Problem with internet all of a sudden 10.04"
date: 2011-07-27
forum: General Help
---

### Post by gibxam on 2011-07-27
Hello All,

I've been using 10.04 with no problems since it was released until a couple days ago. Now my wireless will simply stop working after each new webpage loads. Whats strange is that it will not disconnect me, and the wireless icon in the top right will continue to show that I am connected to the internet. I am currently tethered to my phone and the internet is working fine. Once If I switch to my regular wireless internet and disonnect and reconnect to my home router then the webpage will load fine only once then after that it will not work again until I disconncet and reconnect again. This is not a problem for anyone else in my house who all use macs (needless to say they are all very smug about this). Also when I connect to my schools wireless internet there is not a problem. Also restarting my modem and router at home does nothing to solve the problem. Like I said before this just started up about 3 days ago and has baffled me since. Any help would be much appreciated, below is my iwconfig and lspi output.

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Jake's Meat"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:CB:82:31   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

usb0      no wireless extensions.

```

```

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

```

---

### Post by linuxuser12345 on 2011-07-27
Have you tried restarting your system?

---

### Post by gibxam on 2011-07-27
Yes, restarting my computer gives the same result as disableing and reenabling my network adapter, nameley the first webpage will load fine but all the ones afterwards will not work

---

### Post by linuxuser12345 on 2011-07-27
Try using 10.10 or 11.04

---

