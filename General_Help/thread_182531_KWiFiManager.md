---
title: "KWiFiManager"
date: 2006-05-26
forum: General Help
---

### Post by Ruben123 on 2006-05-26
Hej, I have a big problem with the IP adress when i use my KWiFiManager.
the Lokal IP = unavailable. 
whatever network i use, it still unavailable. 
netwerk, mac and incryption status looks ok.

When i use ubunto i don't have a problem, 1,2,3, and i am online, but with kubunto, mmm, no, i can't fic it.

I also tryed the live Cd of kubunto, and 2 times (of 20 trys) i could go online, but than it also found a local IP

so, couls somone help me.

how can i get the local IP founded???

sorry for my english

---

### Post by faswad on 2006-05-26
Are you connected to a network?

If you are, try running dhcp discover manually and see if it picks up an address:
```
sudo dhclient wlan0
```
where wlan0 is the name of you wireless adpater.

i would recommend using knetworkmanager instead of kwifimanager.
```
sudo apt-get install knetworkmanager
```

good luck.

---

### Post by Ruben123 on 2006-05-26
thanks for you help, but it won't help me that big. 

after i inserted the fist command i got this. 

There is already a pid file /var/run/dhclient.
pid with pid 1 Internet Systems Consortium DHCP Client V3.0.2 Copyright 2004 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP) sit0: 
unknown hardware address type 776 SIOCSIFADDR: No such device 
wlan0: ERROR while getting interface flags: No such device 
wlan0: ERROR while getting interface flags: No such device 
sit0: unknown hardware address type 776 Bind socket to interface: No such device 

after the second command, i got this 
Pakketlijsten worden ingelezen... Klaar 
Boom van vereisten wordt opgebouwd... Klaar 
E: could not find pakket knetworkmanager

---

### Post by faswad on 2006-05-26
What is the ouput of 
```
iwconfig
```

---

### Post by Ruben123 on 2006-05-27
mm, i tink it's not so good :( 

this is the output: 

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"DbllLL"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:BF:00:5D:AC
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=96/100  Signal level=-29 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

sit0      no wireless extensions.

---

### Post by Ruben123 on 2006-05-27
someone told me to set a fixed ip, is that a possibilaty, or wouldn't it help.

and, how you do, if it will help

---

### Post by faswad on 2006-05-27
Ok the output is not bad.

Is y our wireless access point named "DbIILL"?

if so try:
```
sudo dhclient eth0
```

---

### Post by Ruben123 on 2006-05-27
Yes, it's called DbllLL

with a fixed IP it also don't work

---

### Post by Ruben123 on 2006-05-27
I tryed the code sudo dhclient eth0

And that works.

I am now online whireless. so, thank you very much for you time and info

thx

---

