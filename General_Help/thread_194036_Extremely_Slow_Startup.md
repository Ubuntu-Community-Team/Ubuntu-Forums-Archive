---
title: "Extremely Slow Startup"
date: 2006-06-10
forum: General Help
---

### Post by cam2009 on 2006-06-10
Ubuntu was going great for a few days, then one day, I turned it on, it went through the startup screen, then went to a terminal-like screen where it went through another list of startup options (not sure if they were the same thing, I'll check and update). The first screen, which had the ubuntu logo, wasn't any faster, there was just an added screen at the end, like it was doing it all over. It takes at least 45 seconds to get through it. Then, maybe it's my imagination, but it also takes much longer during the rest of the startup, too. Sometimes this happens, and sometimes it goes through nice and fast, though usually it has this problem. I did some tweaking with some guides in here quite a bit, but I'm not sure what ones I really did, or how to undo them, so that could be a problem. Maybe something abnormal in the startup? but that shouldn't make that happen...any ideas?

---

### Post by cam2009 on 2006-06-10
Main list:
* Preparing restricted drivers...
 * Starting basic networking...
 * Starting kernel event manager...
 * Loading hardware drivers...
 * Starting PCMCIA services...
 * PCMCIA not present.
 * Loading manual drivers...
 * Starting RAID devices... 

It's like I'm seeing the system messages that I shouldn't be.

---

### Post by ericesque on 2006-06-11
to me, it sounds like you're simply seeing a non-graphical version of grub.  The pretty splash is just something to look at while grub runs.  If you didn't have a splash, you'd see that black and white text (that you've started to see) each time you boot.  If I recall correctly, it has happened to me a few times too.  That's nothing worth worrying about.

Now, the 45 second boot seems a bit slow.  Try clocking it a few times to see how long it really is.  Post your system specs and we might be able to tell if your boot time is reasonable.

---

### Post by ericesque on 2006-06-11
Just came to mind that the random slow boot may be the result of an update.  Either one of the system updates doing its thing-- or possibly the result of one of your tweaks.  

meh. just report back with your times and specs and we'll see what we can figure out.

---

