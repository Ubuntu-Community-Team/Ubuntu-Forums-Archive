---
title: "Need help setting up wireless PLEASE......."
date: 2010-03-04
forum: General Help
---

### Post by medicalystoned on 2010-03-04
Here is the deal.... my last remaing Windows xp machine crashed, it was set up as the virtual server for my home network.... so the media storage was accessible by all the machines in the house through the wired part of the router..i installed kubuntu 9.04 in that machine and no more windows.... i have a linksys wrtg45 router, it is wired and wireless....

so what i would like to do now is this... first set up the network so i can share the media with other kubuntu machines in the house

the other major problem is my one wireless kubuntu box is just not hooking up with my router. it does say it is connected but then when i open firefox it will not work and disconnects me.....

PLEASE PLEASE HELP ME....... thanks in advance for any advice.

---

### Post by jimbren on 2010-03-04
Here's a couple of things to look at that I've done in the past and have found helpful.  Your mileage may vary.

1) Verify that you actually are connected from within a konsole window.  run iwconfig and confirm your IP address, and that the IP of your router is you default gateway, and then try to ping it.  If you can ping it, you're actually connected to the network and the problem is elsewhere.  

2) Once you're able to ping, install a text browser like elinks and try to browse with that.  I'm not suggesting it's an alternative to Firefox, this is just another step to make sure you're a) connecting, and b) able to browse.  

If you can browse with elinks, then the problem is in firefox and not in your connection.  

If you're not able to browse, post the output if ifconfig.

[QUOTE=

the other major problem is my one wireless kubuntu box is just not hooking up with my router. it does say it is connected but then when i open firefox it will not work and disconnects me.....

PLEASE PLEASE HELP ME....... thanks in advance for any advice.[/QUOTE]

---

### Post by medicalystoned on 2010-03-04
@JIm.... first off, thanks for taking the time to help

Ok, i ran iwconfig and here is the output: please bear with me i had to copy it with and actual pen and paper....


wmaster 0  no wireless extensions
wlan0 IEEE 802.11bg  Frequency: 2.437GHz  access point;  not associated
tx- power= 17 dBm
Retry long limit:7 Rts thr; off  Fragment thr: off
Link quality: 0  Signal level: 0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag: 0
Tx excessive retrie: 0 Invalid misc:0 missed beacon:0



hope you have advice on this... thanks again

---

### Post by jimbren on 2010-03-04
You can copy and paste to and from Konsole, just so you know. 

So, your wireless NIC isn't associating with the access point.  
What wireless card is installed in the computer?

---

### Post by medicalystoned on 2010-03-04
a linksys wireless G, it has been in and out of various machines but this has never been an issue

i know i can copy and paste..... but that is on another machine.. the machine I am on now runs great, however it is wired connection.

i will double check that i plugged in it all the way.... thanks for the help.


Any ideas on how to use the machine that was formerly Win XP, and is now Kubuntu 9.04, as a virtual server the same way i could with windows?

---

### Post by medicalystoned on 2010-03-05
sorry...gotta bump...so   BUMP

---

### Post by medicalystoned on 2010-03-05
last time i will do this i promise....BUMP

---

### Post by Chris Musampa on 2010-03-05
> the other major problem is my one wireless kubuntu box is just not hooking up with my router. it does say it is connected but then when i open firefox it will not work and disconnects me.....
This sounds like a problem I've had recently on two different machines I've setup in different environments (an Acer Revo at work and this Asus laptop at home), very weak/unreliable wireless connections, the solution in both cases was to install WICD instead of the standard network manager - in both cases the wireless connection immediately became rock solid.

---

