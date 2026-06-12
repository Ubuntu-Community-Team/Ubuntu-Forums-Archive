---
title: "sound from speakers and headphones in 9.10"
date: 2009-11-08
forum: General Help
---

### Post by egee on 2009-11-08
hello guys, i'm new to linux and i managed to get everything up and running on my new gateway laptop accept one sound problem.  when i plug in my headphones sound still comes out of my speakers...??

i tried to google a solution but everyone is talking about editing stuff and code i don't understand.  i think the sound card is realtek? any help you can offer is appreciated!

---

### Post by HtechB on 2009-11-08
Got a realtekHD and my problem is rather the opposite, but I think we can share the same short term solution.

I use gnome alsa mixer and it allows me to set manually where the sound comes from.

There seems to be development on the card, like I noticed with Karmic theres a weird new thing that switches of the card when youre not using it... so I'll just keep updating untill it gets solved.

PS: you can just switch off that funtionality in you alsa configuration file, it  may fix your problem... but you wount have that new powersaving thing activated. Back up files b4 u edit them. Have fun...

---

### Post by egee on 2009-11-08
i downloaded the alsa mixer and there isn't any options for where the sound comes out, just one master volume.  However since downloading this i no longer have sound from speakers, its headphones or nothing.  lol :confused:

---

### Post by egee on 2009-11-09
anyone have any other ideas?

---

### Post by egee on 2009-11-10
bump :popcorn:

---

### Post by egee on 2009-11-12
not sure what changed but after updating my system its completely fixed.  speakers go off with headphones plugged in and come back on when the jack is pulled out. i dare to say i have a fully functional Ubuntu laptop that blows my windows 7 partition away! \\:D/

---

