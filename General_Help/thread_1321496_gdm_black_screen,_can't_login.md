---
title: "gdm black screen, can't login"
date: 2009-11-10
forum: General Help
---

### Post by jdavis on 2009-11-10
I turned on my Karmic machine this morning, and logged on fine as usual. I then realised that my Mouse wasn't plugged in correctly, and I lazily pressed the reset switch on my machine to restart.
 
When the GDM login screen reappeared I selected my account and typed in my password as normal. I then pressed login. The screen then went black for a moment and then returned me to the login screen again. I rebooted and repeated this several times, but the machine always throws me straight back to the GDM login screen. If I select failsafe gnome I can access the machine fine, although this is obviously not ideal.
 
Can anyone suggest what the cause of this might be? I'm guessing that perhaps hitting reset while still logging in might have corrupted a file in my /home folder?

---

### Post by jdavis on 2009-11-10
Bumpy Bump...

---

### Post by JOHNNYG713 on 2009-11-10
Hi check to see if your machine (bios) is set to the correct time, I have had a similar problem, And the machines bios time was not right ! Good luck !

---

### Post by jdavis on 2009-11-10
I'm still none the wiser as to what the problem was, but I have fixed it.

I copied the entire contents of my /home/jonathan folder to /home/jonathan/bak and logged off and back on to start again with a fresh user account.

I then slowly copied back each directory (.gnome2 .mozilla .purple etc) logging off and back on a few times, until all my gnome and application settings were restored.

There must have been a rogue file somewhere causing the problem, but I obviously haven't copied it back in the process of restoring my settings, so I'm ok now!

---

