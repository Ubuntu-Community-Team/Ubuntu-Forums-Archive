---
title: "WiFi not working with 11.10/Broadcom card"
date: 2012-04-30
forum: General Help
---

### Post by dtom on 2012-04-30
I am a newbie to the forum and not computer savvy and desperately seeking help.  I have an Acer Aspire 4310 laptop with 11.10 and the WiFi won't work, nor can I connect to the internet through a cable into my WiFi modem, though I do see it searching as the little radar symbol runs up and down with the cable attached.  I've read lots of posts on the issue and can't crack it.

I went to terminal and ran lspci -nn | grep0280 and got 'Broadcom Corporation BCM 4311 802.11 b/g WLAN [14e4:4311] (rev01)'.  

Two questions- first, if I just load Ubuntu 12.04 or some earlier version is my problem likely to go away? and second, if not, since I can't connect to the internet, can I download something onto my partner's Mac laptop running Snow Leopard and transfer it to the Acer via a flash drive? And if so, please step by step, how and what?

Thanks.

---

### Post by morrisasaurus on 2012-04-30
I have had the same problem with installing it on an older laptop, and found that there seems to be a problem with firmware. 
But does your computer even show nearby connections?
Also it may work if you use an Ethernet cable.

---

### Post by dtom on 2012-04-30
The wireless radar symbol does nothing at all.  When I connected a cable to the wireless modem the radar symbol scrolls back and forth, but still doesn't connect.  :confused:

---

### Post by latinlightning on 2012-04-30
Are you dual-booting? If so, check to see if you have any issues connecting from there.

---

