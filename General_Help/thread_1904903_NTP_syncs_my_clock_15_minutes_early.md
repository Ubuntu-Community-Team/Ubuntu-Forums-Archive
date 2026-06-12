---
title: "NTP syncs my clock 15 minutes early"
date: 2012-01-05
forum: General Help
---

### Post by AnttiT on 2012-01-05
I just can't get this. My watch, two cell phones, Windows host (I'm running Ubuntu on Virtualbox), BBC World News, MIKES (the official time in Finland) are all more or less in the same time. 

BUT if I run ntpdate on my Ubuntu guest the result is that it moves the clock ~15 minutes early compared to those sources I mentioned.

I'v tried to sync with ntp.ubuntu.com, 0.fi.pool.ntp.org (I am from Finland), 0.fr.pool.ntp.org (I'm in France at the moment), and 3.us.pool.ntp.org. Every time the result is ~15 min early.

antti@antti-VirtualBox:~$ ntpdate -d ntp.ubuntu.com
 5 Jan 22:16:52 ntpdate[13679]: ntpdate 4.2.6p2@1.2194 Fri Sep  2 18:37:16 UTC 2011 (1)
Looking for host ntp.ubuntu.com and service ntp
host found : europium.canonical.com
transmit(91.189.94.4)
receive(91.189.94.4)
transmit(91.189.94.4)
receive(91.189.94.4)
transmit(91.189.94.4)
receive(91.189.94.4)
transmit(91.189.94.4)
receive(91.189.94.4)
transmit(91.189.94.4)
server 91.189.94.4, port 123
stratum 11, precision -20, leap 00, trust 000
refid [91.189.94.4], delay 0.02740, dispersion 0.00139
transmitted 4, in filter 4
reference time:    d2b08711.7795cf4a  Thu, Jan  5 2012 22:31:13.467
originate timestamp: d2b0871b.f309525b  Thu, Jan  5 2012 22:31:23.949
transmit timestamp:  d2b083c4.5dc5c52c  Thu, Jan  5 2012 22:17:08.366
filter delay:  0.02905  0.02740  0.02747  0.02769 
         0.00000  0.00000  0.00000  0.00000 
filter offset: 855.5865 855.5840 855.5829 855.5819
         0.000000 0.000000 0.000000 0.000000
delay 0.02740, dispersion 0.00139
offset 855.584077

 5 Jan 22:17:10 ntpdate[13679]: step time server 91.189.94.4 offset 855.584077 sec

---

### Post by Paddy Landau on 2012-01-06
What happens when you let Ubuntu just update normally? It should be set to update automatically anyway.

To check, click your clock (in your panel) > Time and Date Settings > Unlock to change these settings > Set the time > Automatically from the Internet. While you are there, check your location is correct.

---

