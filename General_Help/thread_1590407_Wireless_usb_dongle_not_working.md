---
title: "Wireless usb dongle not working"
date: 2010-10-07
forum: General Help
---

### Post by 0pnet on 2010-10-07
I've been using linux for a while now and I bought a usb wifi dongle (TL-WN727N) and when I first plugged it in it didn't seem to work. So I did the usual lsmod and so on and blacklisted a few modules. Now network manager was finally beginning to work, it would connect and then after three seconds it would disconnect and reconnect. I then tried wpa_supplicant but it kept giving me (and still does) "wpa_supplicant association request to driver failed" along with some other stuff. On a whim I decided to install wicd and tada, it worked! Now about a week ago I did the usual update that pops up but when I rebooted wicd wouldn't connect anymore. If I had encryption on my router enabled it would sit there saying ":Verifying" for a while then "Bad Password". If I left my wifi unencrypted it wouldn't get an ip. It connects to my wired router just fine, but it won't connect to my wifi.

Any ideas?

---

### Post by llamabr on 2010-10-07
It's a usb dongle.  Is there a usb wire between the computer and the actual device?  Try plugging the device directly into the computer.

It may also help to see which modules you blacklisted.  I had to:

```
rmmod ehci-hcd
```

But I have a different device from you.

---

### Post by 0pnet on 2010-10-07
It's the same way it was when it was working, plugged directly in. I blacklisted rt2800usb, rt2x00usb and rt2x00lib

---

### Post by 0pnet on 2010-10-08
maybe a bump will help seeing as General Help is flooded with an insane amount of questions

---

### Post by jeanlikethis on 2012-03-05
I have ubuntu 11.10 and installed TP-Link TL-WN727N. 

Follow the instructions from: [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

I found Ralink driver 5370 is much stable and reliable than RT2800usb. Please following the steps of downloading and compiling the driver. I have been suffering from the slow and clogging wifi from rt2800 though it is much easier to enable. 

5370 is the one to go.

---

