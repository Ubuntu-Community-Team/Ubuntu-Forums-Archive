---
title: "Connecting to wireless network"
date: 2009-09-20
forum: General Help
---

### Post by bconover on 2009-09-20
I'm trying to connect to an unsecured WiFi network. My card is wlan0, and I've tried running:

```
iwconfig wlan0 essid linksys
```

and then

```
dhclient wlan0
```

but dhclient just keeps timing out, or dhcpcd does, and dhclient keeps saying something about intervals, but doesn't work.

How do I connect to the network?

I've done this before, but I completely forgot how to :oops:

Thanks a ton!

---

### Post by bconover on 2009-09-20
dang these forums are busy. bump.

---

### Post by bconover on 2009-09-20
btw, right now I'm forced to start X and gnome in order to get Knetworkmanager to connect to a wireless network... I can then stop gnome, but I have to leave X running to keep Knetworkmanager alive and connected. I'd rather avoid this and just do whatever Knetworkmanager does directly in the command line.

---

### Post by mandragor on 2009-09-21
Hi, I used to have a similar script that connected a ralink card to a
WPA-encrypted network, the method I used can be found here:
[https://wiki.ubuntu.com/VidNor#Ralink%20Wireless%20Card%20w/WPA](https://wiki.ubuntu.com/VidNor#Ralink%20Wireless%20Card%20w/WPA)

That might be helpful, or you can try the following which I'm guessing
could work:
```

iwconfig wlan0 up
iwconfig wlan0 essid "linksys"
iwconfig wlan0 commit
dhclient wlan0

```

I think the first line is what you're missing, the line with "commit" could
also be necessary depending on your wireless-card. Let me know if any of
this helps.

---

