---
title: "Ubuntu 10.04 update problems"
date: 2010-05-08
forum: General Help
---

### Post by frogbrains on 2010-05-08
Well, wouldn't you just know it?  I encountered problems when upgrading from 9.10 to 10.04 with update-manager.  What a surprise.  Anyway, here are the problems:
1. Cannot enable desktop effects.  Error appears after searching for drivers.

2. 2-3 minute boot times.  Used to be 40 seconds.  It spends 2 *minutes* in the BIOS before actually starting Ubuntu.

3. The volume controls on my laptop's keyboard now control PCM rather than Master, so everything is horrifically loud past three clicks, and two quiet under that.

4. The bootsplash displays at 1280x800, my monitor's resolution, and looks pretty.  The log in screen, however, switches to what looks like 1024x768.  When I log in it changes back to 1280x800.

Can anyone fix these problems?  I don't want to have to do a fresh install.  I *DID* back up my /home folder before updating, but nothing else.

---

### Post by UsedBits on 2010-06-11
At least your desktop came up, i.e. startx started, or init 5 worked.  My update from 9.10 to 10.04 has been an utter disaster.

Primarily, I get no desktop.  At first the cursor would appear and would be controlled by the mouse, but it was on a black field of view.  In my machinations to remedy the problem, the cursor has now disappeared.

I can ctrl-alt-F1 to see the 'terminal' from which startx was launched (and the associated error messages).  Most of the time.

With each change I make, the error changes.

Even though 10.04 no longer uses xorg.conf, removing it really screws things up.

I might have to resort to blowing away my system and loading 10.04 from scratch, something I'd like to avoid if at all possible.

---

