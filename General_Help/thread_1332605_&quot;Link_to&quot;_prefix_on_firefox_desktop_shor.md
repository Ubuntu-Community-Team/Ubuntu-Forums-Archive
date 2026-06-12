---
title: "&quot;Link to&quot; prefix on firefox desktop shortcuts"
date: 2009-11-20
forum: General Help
---

### Post by tasbury on 2009-11-20
In ubuntu/gnome, firefox pre-pends "Link to" at the beginning of all desktop shortcuts.  Is there any way to make it not do that? 

Truth to tell, I don't even know if it's firefox in the generic sense, the Ubuntu version of firefox, or nautilus, or gnome, and I'm having a hard time chasing it down.

Any help here would certainly be appreciated.

Thank you.

---

### Post by ajgreeny on 2009-11-20
Right click on the launcher and look at Properties to see if you can change the name of the launcher to just "Firefox"

---

### Post by tasbury on 2009-11-21
I had no trouble changing the name "Firefox Web Browser" to "Firefox".  

The command executed is "firefox -P default %u" which I assume is /usr/bin/firefox, which links to /usr/bin/firefox-3.0 and thence to /usr/lib/firefox-3.0.13/firefox.sh and, by circuitous means, apparently ending up at /usr/lib/firefox-3.0.13/firefox.  

But I wouldn't swear to that last, I just eyeballed the script and that's what it looked like.

This is, by the way, the common or garden, default firefox installlation on ubuntu 9.04, but the "Link to " prefix is certainly not restricted to ubuntu v. 9.04 or Firefox v. 3.0.13.

---

