---
title: "wireless problems:  is it kwifi or something else?"
date: 2006-03-24
forum: General Help
---

### Post by insub2 on 2006-03-24
i got Kubuntu on my hp compaq nx6110. the internal wireless card is a broadcom. i use bcmwl5 driver installed with ndiswrapper. (mostly used this thread to do it: [http://www.ubuntuforums.org/showthread.php?t=25683]("http://www.ubuntuforums.org/showthread.php?t=25683"))

i've searched the forums a bit and can't find anything specific to my problem. i open KWiFiManeger and it detects my home network. it says it is connected. i get the wireless status icon in my system tray. BUT i amnot conected to my network! and when i close KWiFi the icon is no longer on my system tray. also, the LED for the wlan on/off button blinks occasionally. 

i'm not familiar with linux or kubuntu enough to know if my problem is with KWiFi or something else.

---

### Post by incubus on 2006-03-24
Are you sure that after connecting you received an IP for your network?

$ sudo dhclient

What do you get from:
$ ifconfig

incubus

---

### Post by mexlinux on 2006-03-24
There are two things none never told me, but that understanding them where a big step for mankind....:
1)wireless conection, means the "virtual cable" between your computer and the router.
2)network connection, means the proper configuration of your network comunication protocols (aka your TCP/IP settings)
You seem to get a proper wireless connection, but not a right TCP settings.

You will find this page very usefull:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

By the way, The only way I have *succesfully* found to get kubuntu working on several wireless networks, is to manually modify 
/etc/network/interfaces
/etc/resolv.conf
and using the commands
sudo ifdown eth1
sudo /etc/init.d/networking stop
wait some seconds and then
sudo /etc/init.d/networking start
...and cross my fingers!
Editings and commands are the way, Any gui tool in kubuntu is incomplete, bugouse or simply pure crap.

Regards,
Miguel

---

