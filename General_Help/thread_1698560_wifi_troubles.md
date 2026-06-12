---
title: "wifi troubles"
date: 2011-03-02
forum: General Help
---

### Post by Beowolf64 on 2011-03-02
I have a dual boot Vista / Maverick laptop. I can connect to WPA2 protected WIFI from Vista, but no success from Maverick. Since Vista works fine, I suppose everything is OK with the adapter and I am using the correct WPA key.

When I click network indicator applet it shows correct SSID, but when I go on and click WIFI it pops ***Connection failed*** window which says ***Was not able to connect to Wi-Fi network. Check your network password.*** But after I entered WPA key into the filed called "passphrase", clicking WIFI icon from the network applet did nothing. It didn't pop any error messages but didn't connect too. Please see the attached to get a better idea.

I already spent an hour trying to get working and goggling for possible solution. Any help from forum members is greatly appreciated. Thank you.


P.S. Ethernet works fine. I could go online with Maverick and download all automatic updates.

---

### Post by Megaptera on 2011-03-02
What's the make of the laptop? Some makes have drivers that need a bit of coaxing.

I like the thread title by the way!

---

### Post by doas777 on 2011-03-02
I've not heard of this "passphrase" file of which you speak. I put my passphrase in network manager, and it saves it (encrypted) in the system keyring.

---

### Post by grahammechanical on 2011-03-02
My eyes see this sentence:

> after I entered WPA key into the filed called "passphrase"

and the only thing that I can suggest is to check that the network manager is set to WPA encryption. If it is set to WEP then the connection will fail.

Oh, I also like the thread title.

Regards.

---

### Post by uRock on 2011-03-02
Use Network Manager.

---

### Post by Beowolf64 on 2011-03-02
Title! Duh! Should be wifi, not wife.

The box is HP Pavilion dv5 with Broadcom 802.11b/g WLAN. It is running 64 bit Maverick.

---

### Post by LetUsDesign.it on 2011-03-02
> **Beowolf64 said:**
> I have a dual boot Vista / Maverick laptop. I can connect to WPA2 protected WIFI from Vista, but no success from Maverick. Since Vista works fine, I suppose everything is OK with the adapter and I am using the correct WPA key.
 
When I click network indicator applet it shows correct SSID, but when I go on and click WIFI it pops ***Connection failed*** window which says ***Was not able to connect to Wi-Fi network. Check your network password.*** But after I entered WPA key into the filed called "passphrase", clicking WIFI icon from the network applet did nothing. It didn't pop any error messages but didn't connect too. Please see the attached to get a better idea.
 
I already spent an hour trying to get working and goggling for possible solution. Any help from forum members is greatly appreciated. Thank you.
 
 
P.S. Ethernet works fine. I could go online with Maverick and download all automatic updates.
 
You may want to check the case sensitivity of your passphrase you are entering. If your router has "AABBCCDDAA" as the key, "aabbccddaa" will not work.
 
Some routers/os combinations are picky. Good luck.

---

### Post by philinux on 2011-03-02
Thread title change to Wifi.

---

### Post by ghostborg on 2011-03-02
It may be a driver issue. I had a Dlink DWA140 that would not connect until I got a driver from the chip maker of my DW140, like Ralink. It had to do with some configuration settings within the driver and I was able to finally find one that was compiled already.
Maybe search the forums for your wireless card.

---

### Post by Beowolf64 on 2011-03-03
Thanks for replays. I think it clear to me how to get wifi working. But when I turn my laptop on it freezes at*** checking battery...*** stage. Googling revealed that quite a few people had the same problem. Top google link leads to this forum. I tired some of the suggestions from this forum but nothing worked for me.

---

### Post by Beowolf64 on 2011-03-03
Another problem. I can't select **Available to all users**. See the attached image.

Network connections don't show in notification area too. I tried reinstalling network manager. Didn't help.

---

### Post by gandaran on 2011-03-03
> **Beowolf64 said:**
> Another problem. I can't select **Available to all users**. See the attached image.

Network connections don't show in notification area too. I tried reinstalling network manager. Didn't help.
the account you are using has the administrator rights?

---

### Post by uRock on 2011-03-03
> **Beowolf64 said:**
> Another problem. I can't select **Available to all users**. See the attached image.

Network connections don't show in notification area too. I tried reinstalling network manager. Didn't help.
You have to actually have to start entering info before it will allow you to have it for all users.

---

### Post by Beowolf64 on 2011-03-03
I am admin and have enabled all privileges for myself.

***Available for all users*** box remains un-selectable even after entering all necessary information. I created several connections (some dummies) and non of the appeared in network manager notification area. In fact there is nothing, except greyed out ***No network devices available*** field. See the attached image.

I tried to use network editor from the terminal and got some strange error messages.

```
**$ nm-connection-editor**

** (nm-connection-editor:3710): WARNING **: get_all_cb: couldn't retrieve system settings properties: (2) The name org.freedesktop.NetworkManagerSystemSettings was not provided by any .service files.

** (nm-connection-editor:3710): WARNING **: fetch_connections_done: error fetching system connections: (2) The name org.freedesktop.NetworkManagerSystemSettings was not provided by any .service files.



[B]$ sudo nm-connection-editor
[/B]
** (nm-connection-editor:3712): WARNING **: get_all_cb: couldn't retrieve system settings properties: (2) The name org.freedesktop.NetworkManagerSystemSettings was not provided by any .service files.

** (nm-connection-editor:3712): WARNING **: fetch_connections_done: error fetching system connections: (2) The name org.freedesktop.NetworkManagerSystemSettings was not provided by any .service files.

```

---

### Post by Beowolf64 on 2011-03-03
I forgot to add that I can go online from that computer. Attached is the portion of syslog taken right after reboot. There are some error messages related to NetworkManager saying ***To report bugs please use the NetworkManager mailing list.***

---

### Post by frenziedfemale on 2011-03-04
> **Beowolf64 said:**
> ....But after I entered [COLOR=DarkRed]WPA key[/COLOR] into the filed called "[COLOR=DarkRed]passphrase[/COLOR]", ....

I use WEP and don't know much about WPA but with WEP the 'key' and the 'passphrase' are not the same thing. Are you sure you have selected the proper security/encryption type to begin with?

---

### Post by Beowolf64 on 2011-03-05
SOLVED. Need to remove connman. Network manager works fine again.

---

