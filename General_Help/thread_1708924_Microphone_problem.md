---
title: "Microphone problem"
date: 2011-03-17
forum: General Help
---

### Post by Trexss on 2011-03-17
Hello,
When i start ubuntu the microphone work, i even can record sound but after a while it just stops and i cant get it to work again.  Please help
im using the newest version of ubuntu x64 right now.
My pc is hp presario cq-61
Thanks

---

### Post by coldraven on 2011-03-17
I don't know if this will help but I had a problem with Skype distorting sound so that I could not be heard.
I had reduced the levels in the Sound Prefs menu but still no good. It was odd because I could see the sound meter working at medium levels.
So I opened a terminal and typed    
     alsamixer 
I noticed that the Master level was in the red, so I reduced it to 75.
Press F4 for Capture, use the L/R arrow keys to go to Internal Mic Boost.
It was set to zero so I increased it with the up/down arrow keys to 33.
Skype is working fine now.

---

### Post by Trexss on 2011-03-18
I'v fixed it, just addet one line to one document.
I'v watched video on youtube and there was a tutorial for that.
Thanks for the reply

---

