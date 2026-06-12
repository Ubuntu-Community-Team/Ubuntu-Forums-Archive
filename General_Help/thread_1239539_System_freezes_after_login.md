---
title: "System freezes after login"
date: 2009-08-13
forum: General Help
---

### Post by penguinguy on 2009-08-13
Jaunty's been running perfectly for months, but now it freezes after logging in.
Everything goes nicely until the login screen. I login with my name/password, the screen goes black with the cursor in the middle (normal). Then the music glitches out and the mouse and keyboard stop working, leaving me stuck on a black screen until I press the restart button on my computer. I've tried several times and it's always been the same.

Live CDs and Windows work just fine. Anybody have any clue what's going on or how to find out?

---

### Post by zkriesse on 2009-08-13
Check this link out and then get back to me if it helped at all. [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by penguinguy on 2009-08-14
> **Zachk18 said:**
> Check this link out and then get back to me if it helped at all. [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

I really ought to remember to check the wiki...
Anyway, I tried disabling compiz and now it gets a little further before freezing. The top panel and the Applications, etc. menu loads, and conky does too. After that it freezes and conky stops updating.
I had already updated my system and rebooted the same day before it started, so a bad update can't be the cause.

Also, now aptitude is yelling at me saying my sources has weird symbols I don't know how to type in them. Is there a terminal command to save a list of installed packages, like when you Save Markings in Synaptic?

---

### Post by penguinguy on 2009-08-15
Well, that software sources thing kinda just fixed itself. I've no idea what I did, but Ubuntu gets a few more seconds further before freezing now.
I tried reading /var/log/dpkg.log, but I had no idea what I was looking at.

---

### Post by penguinguy on 2009-08-20
Well, it's fixed. Here's what I did:
I have no freakin' clue.
fsck decided that this time it checked the drives (which it's done every day since this all started) it would find and fix an error. Then it was just re-enable the graphics driver, reinstall compiz, and tah-dah!

I love Ubuntu. Such a feeling of accomplishment so now I can check my empty inbox in Ubuntu instead of Windows. :)

---

