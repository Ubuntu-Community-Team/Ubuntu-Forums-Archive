---
title: "My skype, she's a no good"
date: 2009-08-06
forum: General Help
---

### Post by gregapan on 2009-08-06
I installed skype for the first time on JJ (I've used it for years on windows), and from the get-go, it has not worked. It will not make any calls. The call window immediately says "Call finished" and "Sound playback error". When I try to make a test call, the same thing happens.

I posted this problem earlier, but got no help on it, so I'm posting it again.

Anyone? :(

---

### Post by credobyte on 2009-08-06
Try changing your sound devices to Pulse ( in Skype settings ).

---

### Post by gregapan on 2009-08-06
We are on the right track, thanks.

Now, just the sound input won't work. I can make a call, but people can't hear me.
I reset all sound devices to Pulse in settings. This seems to be correct, as the test call won't work otherwise. 

However, my sound does not go through. My mic IS working, though, because it gets picked up at least on the pc speaker. 

I've tried to play with the sound settings on ubuntu, like mic boost, but to no avail.

:(

---

### Post by hibliss on 2009-08-06
Try to use pulse for everything except for Mic in, and use you soundcard in for that, for me that is HW audio....

---

### Post by gradinaruvasile on 2009-08-06
Uncheck "Allow Skype to automatically adjust my mixer levels". Because that control doesnt work. It lowers your input level too much. Also i would recommend using alsamixer from a terminal to do the adjustments.

---

### Post by gregapan on 2009-08-06
gradinaruvasile, I tried unchecking that--no effect.

hibliss, I  tried setting input to my audio card. I didnt see the one you mentioned, but used the intel setting (should be right), and... no go.

Still stymied, aaarr. :confused:

---

### Post by gradinaruvasile on 2009-08-06
After unchecking have u looked at your input levels? Cause if Skype sets it, it will remain that way. 
Also use alsamixer (launched in a terminal), the gui sound tools tend to misreport things sometimes.

---

### Post by gregapan on 2009-08-06
Okay, I played around with various settings and seem to have worked it out. :D

Thanks for all your help, everyone!

---

