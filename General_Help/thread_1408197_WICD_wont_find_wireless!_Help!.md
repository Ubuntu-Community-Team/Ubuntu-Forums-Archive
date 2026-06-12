---
title: "WICD wont find wireless! Help!"
date: 2010-02-16
forum: General Help
---

### Post by Link Undead on 2010-02-16
So I just got this laptop... well traded my desktop for it and its a Dell Inspiron 1721. The Wireless was working fin when it had Windows vista on it but when I installed Ubuntu 9.10 The wireless just seemed to not exist. The LED wouldnt even turn on. So I installed wicd and then the wireless icon began working but it still won't find any wireless networks.

Any help is appreciated. Thanks!

---

### Post by nothingspecial on 2010-02-16
You need to post your wireless card -

```
sudo lshw -C network
```

Post the output of that

---

### Post by anaconda on 2010-02-16
Which wlan chip do you have?

I quess it is a broadcom..

but anyway. have you tried the
System>Administration>Hardware drivers
if it suggest a driver for your wlan-card?

lsusb
and 
lspci
commands from terminal will tell you which card you have. And once you know the card, then you can search for its installation tips from these forums

PS: I checked. you have a broadcom chip, which can be made working with ubuntu

---

### Post by nothingspecial on 2010-02-16
Yes according to the internet you have a broadcom 43xx wireless card

```
sudo apt-get install b43-fwcutter
```

Then reboot and you should have wireless.

---

### Post by Link Undead on 2010-02-18
I figured it out after looking through multiple articles and questions I redownloaded ubuntu 9.10 and rebooted the operating system. It seems that multiple people with a fresh install get a much better outcome than just upgrading it. Thanks to all who had helped.

---

