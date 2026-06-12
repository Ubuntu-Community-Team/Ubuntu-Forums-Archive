---
title: "Accidentally removed the red shutdown button - how to get it back?"
date: 2010-05-20
forum: General Help
---

### Post by madmax75 on 2010-05-20
I accidentally removed the red shutdown button from the top panel. How do I get it back?

I did an upgrade from Karmic to Lucid, so I believe I still have the old icons in the top menu. BTW upgrading seems to create an odd mix of the previous version and the new one, maybe I will make a clean install some day...

And no, it is not in the right-click "Add to panel..." menu. There is only the user switcher, which is not what I'm looking for.

EDIT:

Sorry, got it back myself! 

I looked at some of the other answers to the same sort of problem I had and found a way to install the MeMenu (the upgrade did not put that one in the panel either) through Synaptic (in Synaptic, search for "indicator-me"). 

I right-click-added that to the panel, and voila, it brought also the shutdown icon back.

I guess this was just a case of mismatch between the old and new panel icon/applet versions or something like that.

---

### Post by Megaptera on 2010-05-20
Are you sure there's not a shut-down icon that looks like a light switch in the add to panel options? 
I've just checked in 10.04 Ubuntu and it's there on this one.

---

### Post by madmax75 on 2010-05-20
> **Megaptera said:**
> Are you sure there's not a shut-down icon that looks like a light switch in the add to panel options? 
I've just checked in 10.04 Ubuntu and it's there on this one.

No, I don't have that one as far as I can tell.

As I said, I did not do a clean install, but an upgrade. Apparently, the upgrade (at least in my case) just does not replace everything consistently. So what I have is a lot like Karmic, but with stuff from Lucid sort of "glued on" to it. A mutt of a system :)

For example, I had to find a way to install the MeMenu manually, the upgrade did not install it at all. Same with Ubuntu One and Rhythmbox/Ubuntu One Music Store. I had Rhythmbox removed in my old Karmic installation because I didn't need or use it really. I still haven't set up my bank account to work with the Music Store. Seems like an awfully and unnecessary complicated process to me - I apparently have to rig my bank account with Music Store through PayPal :confused:

But, because of the manually added MeMenu, the shutdown works again. :)

---

### Post by efflandt on 2010-05-20
A curiosity is that the shutdown button on my 64-bit 10.04 LTS desktop has always been white, but when I recently installed 32-bit 10.04 LTS on an older laptop, I noticed that its shutdown button was red.

But I noticed the latter (red) after doing updates that required rebooting, and did not pay attention after that.  So is there any significance to the color of the shutdown button (like if the system needs to be rebooted, or something like suspend/hibernate might not work)?

---

### Post by madmax75 on 2010-05-22
Yet another twist: my MeMenu shutdown button does not work either.

Yes, you have the shutdown option there, but all it did was take me back to the login screen.

So, I had to do "sudo shutdown -h now" in the Terminal.

But, after I booted the computer back up the next day, the Big Red ShutDown Button had magically appeared into the "Add to Panel..." menu. Installed it back, and it works.

So I'm back to the original situation now, which is good.

I ditched the MeMenu, though. I find no actual use for it really. Besides, Gwibber does not work right on my system - it keeps freezing on me. So ditching that as well.

---

