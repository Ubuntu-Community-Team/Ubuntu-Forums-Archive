---
title: "reliance modem not connecting"
date: 2011-06-15
forum: General Help
---

### Post by saman6015 on 2011-06-15
Hello every one in this forum I am using Ubuntu 11.04 
 
    I've Reliance Broadband internet modem . very first time only it was connected but next onwards it's not connecting , I am trying last one month to connect internet , I am tired .I had seen lot of thread related to this problem but it's not connecting, my device is identified by network manager and  i entered  user name and password ,connecting process is going on but finally it's not connecting . i installed wv dial and usb modeswith data 




please solve this problem Thanks in advance .

---

### Post by prshah on 2011-06-15
> **saman6015 said:**
>     I've Reliance Broadband internet modem . very first time only it was connected but next onwards it's not connecting

The Reliance broadband USB modem can switch between Broadband+ (HSDPA) and Full Speed (1x CDMA). There is also a Hybrid mode; which will attempt a HSDPA connection, but fallback to 1x if signal is not strong enough.

It is easy enough to switch between modes with the included Windows application.

If you are on an "unlimited" plan, you will have 3.1mbps upto your FUP limit, and then unlimited traffic on 1x speed. If you have crossed your FUP limit, it will not connect unless you change the mode to 1x.

However, I do not know how to do it on linux, though there is a linux "driver" and program included on the USB stick.

You can check this by attempting to connect from a Windows computer using the included dialer application on the usb stick. 

Please post back if you feel this is not your problem.

---

### Post by saman6015 on 2011-06-15
How to switch between high speed mode to hybrid mode

---

### Post by kumaranphoenix on 2011-07-23
I'm not sure how to switch it in linux, but here's how to do it in windows. Just click the desktop icon to launh the UI of the modem. Click settings, there u'll c a drop down box having options(below those optins like ppa settings etc) as 1x,hybrid,broadband+. Select the one of ur choice and click apply.

---

