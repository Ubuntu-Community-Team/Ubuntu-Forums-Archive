---
title: "need help with ettercap"
date: 2010-01-14
forum: General Help
---

### Post by bix15 on 2010-01-14
Hey guys.
As the title suggests, I would like help with a program called ettercap.
The forums on the ettercap website aren't exactly for this kind of support so I thought I'd ask here :)

I'm actually having trouble getting past the very first step of the sniffing proccess X)
I'm running the GTK interface or the graphic version of ettercap if that helps....
So far I have gone to the optins tab and set the netmask to 255.255.255.0
I have absolutely no clue if thats the way it's supposed to be done so if it's not, let me know :)   Now, my problem is when I click Sniff>Unified sniffing...  It asks for a "Network Interface"  and I don't know what to do lol XD
I've looked around and watched some vids....I see it this way, once I can get past this step it's all peachy :)

Can anybody help??
Thanks a LOT!

P.S.  I've tried putting in "eth0" and "eth1"   and still no luck

---

### Post by HPD2 on 2010-01-15
Make sure you are runing the program as root, or that it askes for a password when it starts up.

---

### Post by bix15 on 2010-01-15
Yeah I ran it as root and when I type "eth0" into that box, ettercap closes and my terminal and the terminal gives me an error. Check it out in the attatched screenshots. "ettercap1.png" shows what it looks like before I enter "eth0" into the Network Interface box. "ettercap2.png" shows what happens after I enter "eth0" and press the "Ok" button....

Do you know what's wrong??

---

### Post by bix15 on 2010-01-15
Actually I think I just fixed it....I typed ifconfig in my terminal and chose wlan0 and used that and it works so far....I'll test it later when one of my parents gets on their laptops tonight

---

