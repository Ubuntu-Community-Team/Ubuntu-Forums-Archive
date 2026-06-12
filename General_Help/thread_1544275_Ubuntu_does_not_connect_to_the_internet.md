---
title: "Ubuntu does not connect to the internet"
date: 2010-08-02
forum: General Help
---

### Post by michaelbobe1 on 2010-08-02
I recently installed Ubuntu on dual boot with my win7. I am able to configure my home network, it shows up, however i get no signal and can not connect to the internet. Please help.

---

### Post by killingspree on 2010-08-02
System>admin>hardware drivers
install them all
click the wireless icon on the top-panel and it *should* be there

---

### Post by michaelbobe1 on 2010-08-02
> **killingspree said:**
> System>admin>hardware drivers
install them all
click the wireless icon on the top-panel and it *should* be there

I did just that, a progress screen showed up very quickly and dispareared. I still cannot see any wireless connections.

---

### Post by MasterGamerJK on 2010-08-02
you may have to use "Windows Wireless Drivers" under admin or pref.

---

### Post by protargol on 2010-08-02
Are you trying to connect using wireless or wired connection?  What exactly is showing up but not connecting?  What is your output from ipconfig (run from terminal)?  If you're trying to do wireless, what's your output from iwconfig?

---

### Post by michaelbobe1 on 2010-08-02
> **protargol said:**
> Are you trying to connect using wireless or wired connection?  What exactly is showing up but not connecting?  What is your output from ipconfig (run from terminal)?  If you're trying to do wireless, what's your output from iwconfig?

ipconfig does not work.

iwconfig shows:

lo             no wireless extensions

wlan0  IEEE 802.11bgn  ESSID: off/any
           mode: adhoc   Frequency:2.412 ghz    Fragment thr: off
           tx- power=20 dbm
           retry long limit:7    RTS thr: off         fragment thr: off
           Power management: off

---

### Post by protargol on 2010-08-02
> **michaelbobe1 said:**
> ipconfig does not work.

Sorry.  Try ifconfig.  Too much windows for me.

> 

iwconfig shows:

lo             no wireless extensions

wlan0  IEEE 802.11bgn  ESSID: off/any
           mode: adhoc   Frequency:2.412 ghz    Fragment thr: off
           tx- power=20 dbm
           retry long limit:7    RTS thr: off         fragment thr: off
           Power management: off

What do you see under System> Preferences> Network Connections?

---

