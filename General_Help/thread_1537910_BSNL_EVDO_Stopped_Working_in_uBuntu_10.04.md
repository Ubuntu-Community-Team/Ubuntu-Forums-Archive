---
title: "BSNL EVDO Stopped Working in uBuntu 10.04"
date: 2010-07-24
forum: General Help
---

### Post by The_Big_K on 2010-07-24
Hello,

I have ZTE's 8700 800M EV-DO modem provided by BSNL. It worked like charm on my uBuntu 10.04 LTS. I simply used it through 'mobile broadband' connection in uBuntu. However, few days ago, I had connection problems and technicians from BSNL resolved it. The connection works just fine in Windows 7, but now it does not work in uBuntu.

Now the dialer simply tries to connect and gives up after some time. I've even tried downloading the ZTE's dialer from the official site, but it does not work (connects, but does not work; shows 0kbps all the time). 

What is the recommended way of fixing this? If more information is needed, let me know. I just love to surf the net through uBuntu. 

Awaiting quick response!

---

### Post by dineshs on 2010-07-24
What do you get for```
lsusb
```and
```
dmesg | grep -e "modem" -e "tty"
```when modem is connected and is ON
pl post output

---

### Post by The_Big_K on 2010-07-24
Thanks for your response! :)

lsusb outputs -

```
Bus 002 Device 003: ID 19d2:fffe ONDA Communication S.p.A. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 004: ID 0c45:641d Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


dmesg | grep -e "modem" -e "tty"  Outputs -

```
[    0.000000] console [tty0] enabled
[   12.270082] USB Serial support registered for GSM modem (1-port)
[   12.270158] option 2-1.3:1.0: GSM modem (1-port) converter detected
[   12.270333] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB0
[   12.270363] option 2-1.3:1.1: GSM modem (1-port) converter detected
[   12.270493] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
[   12.270522] option 2-1.3:1.2: GSM modem (1-port) converter detected
[   12.270892] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB2
[   12.270924] option 2-1.3:1.3: GSM modem (1-port) converter detected
[   12.271071] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB3
[   12.271131] option: v0.7.2:USB Driver for GSM modems
```

---

### Post by The_Big_K on 2010-07-25
Apologies for my impatience. Can someone help me resolve this asap?

---

### Post by dineshs on 2010-07-25
try wvdial pl read step 6 onwards in this thread
[http://www.bsnlevdo.in/evdo/setup-bsnl-evdo-usb-modem-in-linux/](http://www.bsnlevdo.in/evdo/setup-bsnl-evdo-usb-modem-in-linux/)

---

### Post by The_Big_K on 2010-07-25
I don't have wvdial on uBuntu 10.04. I guess I'll have to download it first. The most surprizing thing is, EVDO was working alright on the same platform!

I'll try it and post the results soon. Thank you for your quick response.

---

### Post by dineshs on 2010-07-25
There are other methods like ```
sudo pppconfig
```Pl refer these links
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)
Did you try to delete the mobile broadband connection in NM and reconfigure it?

---

