---
title: "Remote Desktop Connects but &quot;freezes&quot;... (well not quite)"
date: 2011-06-03
forum: General Help
---

### Post by Beta_Grumm on 2011-06-03
Hey all.

I set up a tower with 11.04 desktop as a minecraft server and I would like to be able to access it from work for whatever reason.

I set up RPD and checked all the necessary check boxes, opened ports (to the best of my knowledge), installed tightvnc on the remote computer and gave it a go. SUCCESS... almost. It connected and brought up the desktop as desired, however the image seems "frozen". By "frozen" I mean that I am still able to click around and do things on the server, but I just can't see what I'm doing because the remote client isn't "refreshing". It just looks like nothings happening. Example: I move the cursor to the menu bar and click on Applications. It looks like nothing happens however if I walk over to my server, the Applications menu has been clicked and has extended. 
If I log out of the remote client and then reconnect I will see this on the remote box, but nothing after that.

I hope this is making sense. Does anyone have any idea what could be causing this? I have tried this on two separate computers, one that is on the same network as the server (with both local IP and external IP) and the other is at work. Both do the same thing.

Thanks in advance.

---

### Post by Beta_Grumm on 2011-06-03
So I just solved this. 
Turns out there's an old bug that's been around a while. You need to disable the visual effects on the server side or it will cause the remote client to lock up instantly.

To do this on Ubuntu 11.04, I simply logged out, and chose the Ubuntu Classic (no effects) desktop environment and logged back in. Done.

Cheers.

---

