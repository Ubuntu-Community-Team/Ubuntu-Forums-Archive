---
title: "Cant control sound until AFTER local logon??"
date: 2011-06-03
forum: General Help
---

### Post by Plasma2002 on 2011-06-03
TL;DR - 

I can not hear or use sound from command line/ssh unless I log into the desktop first.



In depth description - 

Heres how I can reproduce my problem.
Step 1) Turn on my host computer. I DO hear the ubuntu startup drums
Step 2) SSH into my host computer from another box.
Step 3) Try some basic aplay'ing of sounds from client. Nothing works.
Step 4) Walk back to host, log in on there.
Step 5) Walk back to client. All sound functions work now.


Whats up with that? The sound is obviously WORKING, since I can hear the startup sounds, but why can I not play sounds from a remote client?

This is sounding like a permission issue to me, so I tried editing my group file. I changed this line:
```
audio:x:29:pulse
```
To this:
```
audio:x:29:pulse:root:brian
```

Still did not fix the problem. 

Anybody got any ideas? :(

---

