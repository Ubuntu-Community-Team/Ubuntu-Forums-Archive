---
title: "Where is cd/dvd copy image saved?"
date: 2010-01-06
forum: General Help
---

### Post by wkulecz on 2010-01-06
I did it in 8.04, my question is when I left (opposite) click the desktop CD/DVD icon and select Copy from the pop-up menu where does the extracted image end up.

Its always worked well enough I never worried about it, but today I needed some copies of a DVD a coworker authored that had one of those lame "Stomper" labels stuck on.  It was applied off center and made the disk so unbalanced it appeared to read at 1X or less :(

I was expecting an option to save the image but didn't get one.  Anyone know if its still on my hard drive somewhere so I can avoid the tedium of ripping it again?  Burning four copies took significantly less time that it did to rip.

--wally.

---

### Post by scouser73 on 2010-01-06
Try **/home**

---

### Post by wkulecz on 2010-01-06
Duh, that was the first place I looked.  Nothing was there while it was burning.  There are zillion hidden directories setup by the installer and various application, each with usually multiple subdirs.  Even knowing the name of the burning app from the Gnome desktop popup might be a useful clue.

I suspect it moves around with Ubuntu versions :(

--wally.

---

### Post by J V on 2010-01-06
I'm guessing nowhere... generally you follow up a copy with a paste...

---

### Post by wkulecz on 2010-01-07
> **J V said:**
> I'm guessing nowhere... generally you follow up a copy with a paste...

I'd inserted the burned DVD+R and choose copy from the Gnome desktop icon popup menu.  It then put up a building image dialog message and when complete ejected the disk and prompted me to insert a blank.  I was expecting an option to save the iso when I finished copying but never got one. 

I had hopes someone would know where the temp one was kept assuming it wasn't deleted as soon as I was done copying.  Not a big deal, but I was going to set the iso aside in case they needed more copies later, as usually happens :)

The burns went quickly the extraction was painful.  I guess I'll copy a copy next time to avoid the out of balance label.

I have to say that casual CD/DVD burning on Ubuntu has been a very pleasant experience compard to using Nero on Windows or Roxio on the Mac.

The only thing I miss is Nero's "use multiple recorders" feature  I only have a single burner in my Ubuntu boxes, but this could change if there is good support for writing the same iso image to multiple burners in one step.  Anyone know the name of a package to try?

--wally.

---

### Post by michy99 on 2010-01-07
My guess is that the copy is somewhere in /tmp. Of course, /tmp gets emptied every time you boot, so if that's the case, it may not be there now. Next time, save as a .iso or .img instead of copying.

---

### Post by wkulecz on 2010-01-12
> Next time, save as a .iso or .img instead of copying.

I didn't see that as an option on the desktop icon opposite click popup menu.  Remember this was on 8.04.  

In any event I wasn't expecting it to take so long to read the DVD and make the iso to burn -- that stupid "Stomper" label unbalanced the disk.  As I said, the writes went fast so I'll copy a copy if he needs more down the road, I told him to lose the "Stomper" labels from now on.

I just expected the extracted iso image file to sit some where so I could find and rename it.  System hasn't rebooted or burned more disks so if someone knows where to look I'm still interested in where it might be.

--wally.

---

