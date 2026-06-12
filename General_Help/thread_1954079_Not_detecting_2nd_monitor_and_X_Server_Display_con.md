---
title: "Not detecting 2nd monitor and X Server Display config comes up w/ an error"
date: 2012-04-07
forum: General Help
---

### Post by Eirreann on 2012-04-07
Okay, so I'm very new to Ubuntu; I installed it yesterday and since I installed it and applied the 173 Driver+updates (so that I could use Ubuntu non-2D) my laptop hasn't been detecting my external monitor, which I use because my laptop's screen is pretty screwed up (dis-coloured pixels all over the place).  So I've been scouring Google but since I'm new at this most of the instructions on how to fix this issue don't make any sense to me.
I did try going into Nvidia settings (I am running an GeForce FX Go5200, btw) and accessing X Server Display Configuration, but when I open that up it says:
"Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0. "

And in the "Display" settings it labels my laptop's display as "Unknown" and doesn't even register that I have an external monitor plugged in.
I'm dual-booting Ubuntu alongside Windows XP (if that helps at all).  And I really need the external monitor!

Thanks in advance!

---

### Post by Eirreann on 2012-04-07
Does no one know a work around or fix??

---

### Post by daftlad on 2012-04-07
I had the same problem and I tried a different Nvidia driver till it worked. The only one that works for me is NVIDIA accelerated graphics driver (post-release updates)(version current updates). Hope this helps

---

### Post by Eirreann on 2012-04-07
> **daftlad said:**
> I had the same problem and I tried a different Nvidia driver till it worked. The only one that works for me is NVIDIA accelerated graphics driver (post-release updates)(version current updates). Hope this helps

When I get home from work I'll experiment and see if I can't sort it out.  Thanks for your response!

---

### Post by Eirreann on 2012-04-07
> **daftlad said:**
> I had the same problem and I tried a different Nvidia driver till it worked. The only one that works for me is NVIDIA accelerated graphics driver (post-release updates)(version current updates). Hope this helps


This did indeed help!  When I switched the the Version 93-updates drivers it worked immediately after restarting the computer!  Thanks, mate!
Marking this thread as solved.

---

