---
title: "Madwifi-ng with 2.6.16 kernel problem"
date: 2006-04-14
forum: General Help
---

### Post by gabng on 2006-04-14
Hi, I've just updated my kernel to 2.6.16, and it was all good, however I find that my wireless card stopped showing up in Networking.  So I followed the instructions from [madwifi.org]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") to install the madwifi-ng driver.  
I successfully got ath0 to show up in Networking but wasn't able to get any signals, I typed iwconfig and got this ouput:

```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wifi0     no wireless extensions.

Warning: Driver for device ath0 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

ath0      IEEE 802.11b  ESSID:""
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:380  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I also tried iwlist ath0 scan and got this:

```
Warning: Driver for device ath0 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

ath0      No scan results
```

I don't know what I've done wrong, the driver seemed to have compiled and installed fine. :(  What does the version 19 and 18 mean??  Can somebody please help me out?

---

### Post by gabng on 2006-04-15
Anyone?

---

### Post by gabng on 2006-04-17
I've recompiled and reinstalled the kernel and the madwifi driver, the problem is still there.  So bumping....

---

### Post by testube_babies on 2006-04-17
Have you tried [this tutorial]("http://www.ubuntuforums.org/showthread.php?t=105437")?  It only gave me hell, but it might work for you.

---

