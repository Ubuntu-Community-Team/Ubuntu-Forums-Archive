---
title: "Enable Wireless in Natty Narwhal"
date: 2011-06-04
forum: General Help
---

### Post by Alecazam3568 on 2011-06-04
How do I enable wireless in Natty Narwhal? When I type in "lshw" it tells me: 

*-network=DISABLED

How do I enable wireless? I'm going crazy trying to figure it out!

Also, My Ubuntu has absolutely no Internet. Not even an Ethernet connection. I'm using my Windows for my Internet right now. So, thanks in advance. I think after this I'll finally be able to connect :D

---

### Post by jamesisin on 2011-06-04
Which desktop environment are you using?

---

### Post by Alecazam3568 on 2011-06-04
I'm using Unity

---

### Post by jamesisin on 2011-06-04
Have you tried issuing the terminal command:

```
sudo ifconfig wlan0 up
```

---

### Post by Alecazam3568 on 2011-06-04
Actuallt I have. But I found out why I can't connect. It's not that wireless is disabled. It's already up. I'm missing the firmware for my network card. Thanks though :)

---

### Post by jamesisin on 2011-06-04
That would be a problem.  You may have to connect wired in order to download the appropriate wireless driver.  If you connect via wire and at the same time attempt to access a wireless network, Ubu should automatically attempt to get the correct drivers set up for you.

---

### Post by Alecazam3568 on 2011-06-04
Alright, thank you so much :D

---

### Post by evansgw on 2011-06-08
> **jamesisin said:**
> Have you tried issuing the terminal command:

```
sudo ifconfig wlan0 up
```

I just tried this and it said 

SIOCSIFFLAGS: Operation not possible due to RF-kill

Any suggestions?

---

### Post by Dr Heelhook on 2011-07-19
> **jamesisin said:**
> That would be a problem.  You may have to connect wired in order to download the appropriate wireless driver.  If you connect via wire and at the same time attempt to access a wireless network, Ubu should automatically attempt to get the correct drivers set up for you.

I have problems with this as well. I have connected via wire, and the Internet works, but it still says: "Wireless networks, Device not ready, firmware missing" in gray letters in the Network menu and I can't do anything there.

---

### Post by gandaran on 2011-07-19
> **Dr Heelhook said:**
> I have problems with this as well. I have connected via wire, and the Internet works, but it still says: "Wireless networks, Device not ready, firmware missing" in gray letters in the Network menu and I can't do anything there.
have you looked in additional drivers to activate wireless drivers?

---

