---
title: "Wireless internet???"
date: 2006-05-11
forum: General Help
---

### Post by kharma on 2006-05-11
Hey everyone, This is my first post and i just installed Ubuntu 5.10 on my PC. I was wondring how i can install a wireless LAN on my pc. The lan is a Linksys wireless\b usb network adapter and there are 3 other users on the lan. The internet is linked through the main household computer and is sent wirelesly to my computer. 

Does anyone know how to install it? or know where i can find a tutorial for it?

---

### Post by Dr. Nick on 2006-05-11
[quote=kharma]Hey everyone, This is my first post and i just installed Ubuntu 5.10 on my PC. I was wondring how i can install a wireless LAN on my pc. The lan is a Linksys wireless\b usb network adapter and there are 3 other users on the lan. The internet is linked through the main household computer and is sent wirelesly to my computer. 

Does anyone know how to install it? or know where i can find a tutorial for it?[/quote]

We really need the model number of the adapter, or the chipset if known. I have a linksys B and it is easy to set up with either the wlan-ng drivers or ndiswrapper. Mine is wusb ver 3 using a prism 2 chipset

---

### Post by kharma on 2006-05-11
The model # is WUSB11 Ver 2.8

---

### Post by Dr. Nick on 2006-05-11
[quote=kharma]How would i find out that information?[/quote]

Look on the bottom of the card under the velcro deal if it has one. it should have a model number their, or unplug it and plug it in and run ```
dmesg
``` from a terminal and it should say in teh last few lines what card it is.

---

### Post by kharma on 2006-05-11
[QUOTE=Dr. Nick]Look on the bottom of the card under the velcro deal if it has one. it should have a model number their, or unplug it and plug it in and run ```
dmesg
``` from a terminal and it should say in teh last few lines what card it is.[/QUOTE]

The model # is WUSB11 Ver 2.8

---

### Post by bionnaki on 2006-05-11
[https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11?highlight=%28WUSB11%29](https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11?highlight=%28WUSB11%29)

---

### Post by kharma on 2006-05-12
I have followed the link and done everything it says to do. 

However, Ubuntu recognizes my wireless conection but i still cant get firefox to go out to the internet. What can i do about this?

---

### Post by Dr. Nick on 2006-05-12
[quote=kharma]I have followed the link and done everything it says to do. 

However, Ubuntu recognizes my wireless conection but i still cant get firefox to go out to the internet. What can i do about this?[/quote] 
When you say recgonize do you mean it is listed under the system-administration-networking? 

Launch a terminal and run these 3 commands and post the output if it doesnt work

sudo ifup wlan0  (activates wireless card)
ifconfig wlan0    (shows mac adress and Ip?subnet/gateway if any)
sudo dhclient wlan0      (Tried to get a ip via dhcp)

Also it would be best to login to your router and disable all securiy such as wep/wpa just until you get it working. Also if you have a wired ethernet card aswell you might run 

sudo ifdown eth0  (disables your ethernet card, sudo ifup re-enables)

Prior to the above 3 commands.

Good Luck

---

### Post by kharma on 2006-05-13
Awesome thanks, i will go ahead and try that

---

### Post by kharma on 2006-05-15
[QUOTE=Dr. Nick]When you say recgonize do you mean it is listed under the system-administration-networking? 

Launch a terminal and run these 3 commands and post the output if it doesnt work

sudo ifup wlan0  (activates wireless card)
ifconfig wlan0    (shows mac adress and Ip?subnet/gateway if any)
sudo dhclient wlan0      (Tried to get a ip via dhcp)

Also it would be best to login to your router and disable all securiy such as wep/wpa just until you get it working. Also if you have a wired ethernet card aswell you might run 

sudo ifdown eth0  (disables your ethernet card, sudo ifup re-enables)

Prior to the above 3 commands.

Good Luck[/QUOTE]

Thank you so much IT WORKED!!!

---

### Post by .Maleficus. on 2006-07-28
I just tried the above guide, and now Networking doesn't even detect my wireless.  What do I do?


Edit:  Also, before trying this, I had a wlan0, eth1 and eth0 as my interfaces.  Now, I have the eth0, but it changed my eth1 to eth2 and I don't have the wlan0.

---

