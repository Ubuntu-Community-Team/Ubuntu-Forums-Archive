---
title: "Linux Newbie Installed on Fujitsu A1010 Lifebook"
date: 2006-03-05
forum: General Help
---

### Post by pdiminico on 2006-03-05
I have searched the forum but, since this is my first attempt with Linux I am having a difficult time with enabling my built-in WIFI. 

In the Device Manager I see the USB XI726 PRISM2 WIFI wlan0 device. 

My Ethernet adapter is available in the Network Setting but, the WIFI is not listed to configure?

How can I enable and configure the wlan0 adapter?

---

### Post by issueperson on 2006-03-05
try running system > administration > networking.
see if you wireless connection is listed on the connections tab.  if it is, select "activate." (this might take a while)

after this, you may need to change the properties of the wireless card.  Select "Properties" and then see if the wireless network you want is in the "Network name (ESSID):" box.  if it isn't, click on the drop down arrow and see if the wireless connection you want and select it.  Ubuntu should autodetect any wireless networks in range and put them on that drop down menu.

once that's all set up right (you may not need to change anything) hit "ok" and wait a while again.

Also, under connection settings, i have DHCP selected under my configuration.  if it doesn't work the way you have it already set up, you might come back and change it.  in case you don't know, if you have DHCP enabled you will not need to fill in the other three options below it.  DHCP is the protocol which automatically assigns you an IP address.

let me know if that works.
issueperson

---

### Post by pdiminico on 2006-03-05
**try running system > administration > networking.
see if you wireless connection is listed on the connections tab. if it is, select "activate." (this might take a while)**

This is the problem, I do not have the wireless conection listed.

I have tried to reinstall the ndiswrapper:

Here are my steps and the results.

sudo ndiswrapper -l
xi726 driver present, hardware present

sudo ndiswrapper -e xi726

sudo ndiswrapper -l
No drivers installed

I have the INF and all drivers from the XP version in a WirelessLAN subfolder in Home.

sudo ndiswrapper -i XI726.INF
Installing xi726

sudo modprobe ndiswrapper

sudo ndiswrapper -m
modprobe config already contains alias directive

iwconfig

lo        no wireless extensions.

eth0    no wireless extensions.

wlan0  no wireless extensions.

sit0     no wireless extensions.


ifconfig will list eth0 and lo nothing else.

My system > administration > networking still does not display a wireless conection.

What next?

---

### Post by pdiminico on 2006-03-05
Thanks to this forum I was able to resolve this. All that was needed was to add ndiswrapper to the /etc/modules  and sudo gedit /etc/network/interfaces to add wlan0.

Thank you for your help and on to the next issue.

---

