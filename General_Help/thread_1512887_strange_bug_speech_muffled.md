---
title: "strange bug speech muffled"
date: 2010-06-18
forum: General Help
---

### Post by avcar on 2010-06-18
Hi all i have ubuntu 10.04 with xbmc installed when i play music file or a movie with music on it plays fine however if anyone is talking can still hear background sounds but the speed is very muffled, any ideas this is driving me nuts oh its through optical out on r3610 to my amp.
 
before i wasnt even getting any sound at all through optical until i tried this 
*What worked for me was to go to System->Preferences->Sound Click on the Hardware tab and change it to Analog Stereo Duplex. I know it sounds weird but it works... at least on my machine.*
 
*Then I ran "gstreamer-properties" from the terminal and changed the Audio Plugin to ALSA,, for Device I put it to Digital.*
 
any ideas people? :confused:

---

### Post by avcar on 2010-06-26
anyone?

---

