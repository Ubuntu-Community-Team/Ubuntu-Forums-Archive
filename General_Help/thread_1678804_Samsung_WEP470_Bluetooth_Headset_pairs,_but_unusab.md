---
title: "Samsung WEP470 Bluetooth Headset pairs, but unusable."
date: 2011-01-31
forum: General Help
---

### Post by mrtomservo on 2011-01-31
Hello, I have a bluetooth headset that I just can't seem to set up under Ubuntu 10.04LTS x64.  The dongle is: Bus 005 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter.  The headset is a Samsung WEP470.  I have paired the headset to both my PS3, and my LG phone easily.

Using the gnome-bluetooth applet, I can pair Ubuntu to the headset, and it correctly sees it as a headset.  However, that is as far as I can get.  Nothing shows up in either the pulse-audio volume tool, or the pulse-audio-device-chooser.  I have followed a few howto's that state you need to get pulse-audio to load certain bluetooth modules before it can sink/source to the headset.  

pactl load-module module-bluetooth-device profile=a2dp sink_name=WEP470 address=00:0D:E6:73:B9:84

Always results in:
"Failure: Timeout" 

I'm not sure where to go from here.  Any help would be greatly appreciated.

---

### Post by vipseixas on 2011-04-13
> **mrtomservo said:**
> Hello, I have a bluetooth headset that I just can't seem to set up under Ubuntu 10.04LTS x64.  The dongle is: Bus 005 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter.  The headset is a Samsung WEP470.  I have paired the headset to both my PS3, and my LG phone easily.

Using the gnome-bluetooth applet, I can pair Ubuntu to the headset, and it correctly sees it as a headset.  However, that is as far as I can get.  Nothing shows up in either the pulse-audio volume tool, or the pulse-audio-device-chooser.  I have followed a few howto's that state you need to get pulse-audio to load certain bluetooth modules before it can sink/source to the headset.  

pactl load-module module-bluetooth-device profile=a2dp sink_name=WEP470 address=00:0D:E6:73:B9:84

Always results in:
"Failure: Timeout" 

I'm not sure where to go from here.  Any help would be greatly appreciated.

Same problem, I am starting to think that this dongle does not support A2DP.

---

### Post by AntontheGreek on 2011-04-24
I have gotten it onto the Pulse Audio Sound Settings, but no sound

Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

Samsung WEP 470
Ubuntu 10.10

---

### Post by AntontheGreek on 2011-04-24
> **vipseixas said:**
> Same problem, I am starting to think that this dongle does not support A2DP.

Is that also with Samsung WEP 470? You should only get 
Telephony Duplex HSP/HFP with a standard BT earpiece

---

### Post by cherry316316 on 2011-06-17
my ubuntu 11.04 is not even detecting WEP490 samsung :(

any solution ?

---

### Post by cherry316316 on 2011-06-17
> **cherry316316 said:**
> my ubuntu 11.04 is not even detecting WEP490 samsung :(

any solution ?

update: i should have read the manual first. it says, first time when i use the bluetooth, it goes in pairing mode, if i want to pair again with another device, i will have to do pairing mode again.
now it works like charm.

i also used gchat and my bluetooth device to call a friend and it works like charm.
i can even listen youtube etc songs using my bluetooth without using headphones. 

nice, love the ubuntu :)

---

### Post by mrtomservo on 2011-06-17
That's awesome Cherry!  Glad you were able to get it to work.  Was it the WEP470 or WEP490 you had?  I never did get the WEP470 to go beyond connecting, and eventually gave up. Gave it to a friend and picked up an LG HBM235, which also works fine in Ubuntu 11.04.  Thanks for posting that it worked, glad you enjoy Ubuntu! :)

To anyone interested, I think the problem with Ubuntu 10.04.2lts and the WEP470 had something to do with the module or driver that pulseaudio tries to load when the WEP470 is connected.

---

### Post by cherry316316 on 2011-06-17
mine is 490.

yeah, so may be this is latex version.
also, can u check 470 with ubuntu 11.04 ?

---

