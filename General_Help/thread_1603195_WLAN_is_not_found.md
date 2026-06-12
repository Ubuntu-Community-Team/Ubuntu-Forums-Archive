---
title: "WLAN is not found"
date: 2010-10-22
forum: General Help
---

### Post by nearlymagicman on 2010-10-22
This is a copy from my old thread which is solved but in which i started a new topic: I need(ed) help with my wlan, because my netbook doesn't see my HomeWlan, but like every other int he neighborhood. 
I am using a live-usb atm because i want to check if everything works out bevor i completely install ubuntu.

Details: I want to use my home-WLAN but Ubuntu doesn't see it, which is quite fascinating because it does see a bunch of other which belong to the neighbors. The second quite interesting part is that when i switch to windows i can connect without any problems (and yes it does see it as well).
Any clues what might cause that behavior?
My only guess is that the adapter broadcasts on a false Channel, but i aint sure about that. I entered "sudo iwlist chan" and the output is:
```

lo     no frequency information
eth0   no frequency information
eth1   14 channels in total; available frequencies :
       //bunch of frequencies
       current channel 1
```
So i guess my adapter broadcasts on channel 1, but my router does on channel 6 (I am sure about that part).
But when i tried to "fix" it with "iwconfig eth1 channel 6" and then i check the channels again, it is still on the same on (Channel 1).
Well, i do have a second guess but this one seems even more unrealistic than the first one, it might be possible that my adapter isn't strong enough to get the signal, even though there are just like 2 1/2 Walls between. But this scenario is really unlikely because my netbook is getting so much other signals.

thank you for your fast and helpful help

---

### Post by utilitytrack on 2010-10-22
Can you provide here:
```
$ uname -a
$ ifconfig -a
$ lspci -nn
# iwconfig
```

If I understand, the AP with ESSID "HomeWlan" it's your own router?

---

### Post by nearlymagicman on 2010-10-22
Well the SSID is not HomeWlan, but yes it is mine and is placed like two rooms next to me.

```
uname -a : Linux Ubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
ifconfig -a : way to much to copy, is there smth particular you are interrested in
lspci -nn : same as before
iwconfig  : lo  no wireless extensions

th0  no wireless extensions

eth1 IEEE 802.11 Access Point: Not-Associated
     Link Qualitiy:5 Signal level:0 Noise level: 160
     Rx invalid nwid: 0 invalid crypt: 0 invalid misc: 0
```

---

### Post by Hippytaff on 2010-10-22
try
 
```

lscpi -nn | grep wireless

```
 
:-)

---

### Post by utilitytrack on 2010-10-22
**nearlymagicman**

Don't listen to mr. Hippytaff, do so:
```
$ lspci -nn | grep -E -i 'Network|Wireless'
$ ifconfig -a
```

because "same as before" doesn't tell me anything.

---

### Post by nearlymagicman on 2010-10-22
Hippytaff: no response and no change. What should this command do?

utilitytrack: ```
Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev01)
```


Is there any chance that the adapter might filter between WEP and WAP/WAP2 connections?

Well there is another problem now, it seems related though. I wanted to connect my netbook via cable, but cable is not recognized by ubuntu. So my guess is that the driver for the network adapter is not working correctly.

---

### Post by nearlymagicman on 2010-10-22
Well to anybody who has this problem later and finds this thread:

It is the channel, i changed it to one and, oh my gosh, it worked fine. Atm i am just looking for a way to change the channel of the adapter so other user wont be affected.

---

### Post by Hippytaff on 2010-10-22
Glad you sorted it...my grep command was wrong :-s I wasn't at my ubuntu box to test it first :-)

---

