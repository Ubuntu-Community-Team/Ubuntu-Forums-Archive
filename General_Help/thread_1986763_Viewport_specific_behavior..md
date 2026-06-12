---
title: "Viewport specific behavior."
date: 2012-05-25
forum: General Help
---

### Post by spiritech on 2012-05-25
i was wondering how i would go about setting up viewport specific behavior.

for example. if i open firefox, banshee or say ccsm on viewport 2 i would like them to open at a specific size and position. 
if i then switch to viewport 1 and open say firefox, nautilus and "search for files" then i would like them to open at different size and position. 

i should imagine the code i would be looking for be along the lines of

if viewport 1
      nautilus size 000x000 position 000x000
      firefox size 000x000 position 000x000

if viewport 2
      firefox size 000x000 position 000x000
     banshee size 000x000 position 000x000

i have set up some behavior in compiz manager using the placement tool. however it is restrictive to just the one instance.
and to top it all off i would like to be able to set a second instance. so, say i open two apps the same on viewport one, they are set to different positions.

i can post i screen shot if anyone thinks they can help.

spiritech

---

### Post by spiritech on 2012-05-25
i have started using the wmctrl program to achieve something along the lines i want, although the option i am using does not seem to be working. i have a nautilus window open and i use the code below and nothing happens.

wmctrl -r nautilus -e 0,38,550,919,432

i have checked another thread and the code looks correct.

---

