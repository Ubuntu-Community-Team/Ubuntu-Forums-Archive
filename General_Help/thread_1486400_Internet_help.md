---
title: "Internet help"
date: 2010-05-17
forum: General Help
---

### Post by Umac on 2010-05-17
A few days ago I made the choice to switch from Mac OS X to Ubuntu 10.04, and I gotta say, it was a good choice. The only problem was that it wouldn't detect any wireless connections, so I plugged in my ethernet. It didn't automatically detect my ethernet settings so I went to the edit connections menu and messed around with that. I finally got it working after I changed DHCP on the IPv4 settings to Link-Local only. Then I opened Firefox and it said it could not connect to the server. I contacted my ISP and they said that my connection was definitely DHCP. I applied DHCP settings again, but still no luck. I finally just gave up and installed OS X again, but I also read somewhere that reinstalling Ubuntu from the disk might work but I wanted to see what other people had to say about this.

---

### Post by oldfred on 2010-05-17
Do you have a router? If not you will never have wireless. (Unless you are 'borrowing' your neighbors).

What settings are in the Mac?

If you have a router your settings are to be to the router and the router connects to your ISP.

---

### Post by marshmallow1304 on 2010-05-17
DHCP should work without changing any settings.  What happened in the network manager in the taskbar when you plugged in the cable?  Link-local definitely isn't the right setting for this situation.  If the ethernet works in OS X, you can post the output of
```
ifconfig
```
which might give us a clue if you need a strange setting.  Also, if you boot from the CD and use the 'Try Ubuntu without making any changes...' option, it'll be far less time consuming to test.

---

### Post by Umac on 2010-05-17
> **oldfred said:**
> Do you have a router? If not you will never have wireless. (Unless you are 'borrowing' your neighbors).

What settings are in the Mac?

If you have a router your settings are to be to the router and the router connects to your ISP.

Yeah, I have a Netgear router connected to my modem. 

My mac automatically detected my wireless settings, if that's what you mean.

---

### Post by Umac on 2010-05-17
> **marshmallow1304 said:**
> DHCP should work without changing any settings.  What happened in the network manager in the taskbar when you plugged in the cable?  Link-local definitely isn't the right setting for this situation.  If the ethernet works in OS X, you can post the output of
```
ifconfig
```
which might give us a clue if you need a strange setting.  Also, if you boot from the CD and use the 'Try Ubuntu without making any changes...' option, it'll be far less time consuming to test.

Yeah, I'll post the results for that right now.

EDIT: I didn't get the ifconfig info but when in the trial mode of Ubuntu it did ask me to install wireless drivers. Yet when I installed a few days ago it didn't tell me any drivers had to be installed. I'm thinking this has something to do with it.

---

### Post by Umac on 2010-05-21
bumping this topic, thinking about reinstalling ubuntu, should I go on?

---

### Post by Umac on 2010-05-21
Good news, I'm typing this from Ubuntu 10.04. It turns out I only had to install the wireless drivers. The thing is I'm on the trial version of Ubuntu, and don't know if I'll be able to install the drivers once I install it fully.

---

### Post by oldfred on 2010-05-21
If you look under System, Administation, Hardware Drivers - does it suggest a driver?

---

### Post by akakingess on 2010-05-21
You should be able to, and if you run into further issues with Firefox, I have read in other posts that disabling IPv6 has helped solve some issues. Good Luck!!

---

### Post by Umac on 2010-05-21
> **oldfred said:**
> If you look under System, Administation, Hardware Drivers - does it suggest a driver?
Not last time I installed Ubuntu

> **akakingess said:**
> You should be able to, and if you run into further issues with Firefox, I have read in other posts that disabling IPv6 has helped solve some issues. Good Luck!!

Okay, thanks for the advice and luck

---

