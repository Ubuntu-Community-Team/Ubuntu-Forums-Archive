---
title: "Making my laptop a wifi AP?"
date: 2010-09-15
forum: General Help
---

### Post by Esahp on 2010-09-15
Right now I have WPA2-Personal set on my normal wifi router, but the Nintendo DS Lite only supports WEP encryption. Is there an easy way to make my laptop (Ubuntu 10.04) act as an access point and accept connections (preferrably only one) using WEP encryption, so my NDS will be able to get online?

---

### Post by mikewhatever on 2010-09-15
Adhoc network?
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)

---

### Post by Esahp on 2010-09-16
I tried that, and looked around for some other examples, but couldn't get it working. I think I may know why, though. Would I need to have another NIC connected (as in both eth0 and wlan0) so the NDS connecting to wlan0 could use internet (from eth0) ?

If so, that's my problem then, because I don't have any unused ports on the router. I'll work on clearing that up, I think I *might* have a switch laying around somewhere, but incase I don't is there any other way to approach this issue without buying another NIC?

---

### Post by infocop411 on 2010-09-16
You do need two interfaces, as you mentioned, you could also use two wireless cards if you have a 2nd wireless card lying around

I'll keep an eye on this thread, I have additional ideas that should help you.

---

