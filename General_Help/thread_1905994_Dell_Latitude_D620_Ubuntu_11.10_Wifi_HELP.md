---
title: "Dell Latitude D620 Ubuntu 11.10 Wifi HELP"
date: 2012-01-08
forum: General Help
---

### Post by XAviierG on 2012-01-08
I have a dell latitude d620 that im dual booting window xp and ubuntu on. I had 10.04 and everything went well. I formatted the drive and freshly installed 11.10 but now no matter what I do I cannot connect to wifi. I can only connect to it on Windows XP. Please help me.

---

### Post by XAviierG on 2012-01-08
Anybody?

---

### Post by bkratz on 2012-01-08
Without knowing what the wireless card is, it is a bit hard to help.
Try to enter the terminal mode and copy/paste the output of what you receive from the command

lspci -nn | grep -e 0280 -e 0200

(that is LSPCI in lowercase.)

---

### Post by XAviierG on 2012-01-08
Hi thanks for the reply it is, Broadcam Corporation BCM4311 802.11a/b/g

---

### Post by bkratz on 2012-01-08
> **XAviierG said:**
> Hi thanks for the reply it is, Broadcam Corporation BCM4311 802.11a/b/g


Here is the best post I have seen about this card and either 11.04 or 11.10.  It works.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by XAviierG on 2012-01-08
Ok so I finally got wifi showing in the network tab but now when I enter my password for my wifi it wont connect it will just keep trying to connect and keep asking for the password.

---

### Post by SoldierBoy3000 on 2012-01-08
It sounds like your problem might have something to do with the dual boot. I am running the same exact hardware and it works like a charm.

---

### Post by bkratz on 2012-01-08
> **XAviierG said:**
> Ok so I finally got wifi showing in the network tab but now when I enter my password for my wifi it wont connect it will just keep trying to connect and keep asking for the password.

To see if you can really connect you might try removing (temporarily) the encryption on the router or try at some other location that has free internet service. If you then can connect successfully you may need to try a different encryption method (say wpa2 rather than wpa). Please make sure the router is not in mixed mode (wpa/wpa2) but in one or the other. Also, at the router make sure that your router allows connection to the mac address of your card.

---

### Post by XAviierG on 2012-01-08
> **bkratz said:**
> To see if you can really connect you might try removing (temporarily) the encryption on the router or try at some other location that has free internet service. If you then can connect successfully you may need to try a different encryption method (say wpa2 rather than wpa). Please make sure the router is not in mixed mode (wpa/wpa2) but in one or the other. Also, at the router make sure that your router allows connection to the mac address of your card.

Finally!!!! Thanks all!!!!!!!!

---

### Post by XAviierG on 2012-01-08
Ok so its connecting and Im having connections but im also getting random drops every few seconds

---

### Post by XAviierG on 2012-01-08
Ok I enter the correct password the wifi indicator keeps blinking then the wifi password box comes up again asking me to put the password in. Anybody want to teamviewer and help me?

---

### Post by BertN45 on 2012-01-08
Check "additional drivers" from the dash and make sure that the Broadcom STA driver is NOT activated.

ELSE

I suggest you go to the network applet, edit connections. Goto the wireless tab and delete the wifi network(s) that give you problems or if possible delete all. Reboot and make sure that wireless is enabled in the network applet and try the password again when requested.

---

### Post by XAviierG on 2012-01-08
> **BertN45 said:**
> Check "additional drivers" from the dash and make sure that the Broadcom STA driver is NOT activated.

ELSE

I suggest you go to the network applet, edit connections. Goto the wireless tab and delete the wifi network(s) that give you problems or if possible delete all. Reboot and make sure that wireless is enabled in the network applet and try the password again when requested.

Ok so I removed the STA driver and it finally connected. But why is it keep dropping signal after so often?

---

### Post by XAviierG on 2012-01-08
Sir thank you SO MUCH!!!!!! Its finally connecting and holding good! THANKS!!!!!!!

---

