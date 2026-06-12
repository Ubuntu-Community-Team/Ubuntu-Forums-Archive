---
title: "how to diagnose random problems?"
date: 2009-12-18
forum: General Help
---

### Post by rebeltaz on 2009-12-18
I have no clue what I did, but this system has become unstable as ^%(^! 

What I did do is try (unsuccessfully, at first) to transfer MP3s to a Sansa E250 player. I fixed that by changing USBMode from MTP to MCS on the player. I also enabled file sharing on a secondary hard drive and my home directory. 

Since I did those things, Nautilus would at times refuse to run as would Firefox. I fixed that by deleting the gvfs-metadata directory. Now Firefox will sometimes just shutdown mid way with now rhyme or reason. Last time I tried to run it again and the system (or maybe the X Server?) just kept restarting. I had to CTRL-ALT-F1 to get to a terminal so I could so a shutdown to get out of that. 

I am really at my wits end here. I feel like I am back in Windoze!

Is there anyone that can help me with this? Thanks...

---

### Post by Cheesemill on 2009-12-18
The first thing I'd check is the RAM, just select Memtest when you boot the machine and let it run for several passes, preferably overnight.

---

### Post by Chesamo on 2009-12-18
Have you tried deleting the ~/.mozilla directory? This should restore the default settings and fix the FF crashes.

---

### Post by rebeltaz on 2009-12-18
> **Chesamo said:**
> Have you tried deleting the ~/.mozilla directory? This should restore the default settings and fix the FF crashes.

I will try that tomorrow.


> **Cheesemill said:**
> The first thing I'd check is the RAM, just select Memtest when you boot the machine and let it run for several passes, preferably overnight.

As in from the grub menu? For some reason, there's no option on my PC to even select a grub menu like there is on my laptop. Is there another way?

---

### Post by Cheesemill on 2009-12-18
Pressing either shift or esc (depending on your version) should get you the grub menu.

---

### Post by rebeltaz on 2009-12-21
Well, I'll be a... ](*,)

Shift did the trick and from there I found that my RAM was, in fact, faulty! It was intermittent apparently, the errors were never in the same location twice. I stuck a small stick in there until I can get them replaced (they're Crucial lifetime warranty) and I let MemTest run that over the weekend. Hopefully I'll be good to go tomorrow morning!

Thank you all, so much....

---

