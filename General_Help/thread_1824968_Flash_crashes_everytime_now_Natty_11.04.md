---
title: "Flash crashes everytime now Natty 11.04"
date: 2011-08-14
forum: General Help
---

### Post by gahyoujerk on 2011-08-14
I can't watch youtube or hulu or listen to music on flash sites anymore at all.  I'm running Natty with a dual-boot setup and I wasn't having any problems about a month ago, but I started only running windows for a while more often, but now when I play around with Ubuntu, flash will not work on any site in FF or Chrome.  Each time it says: 'The following plugin has crashed, Shockwave Flash'.

I've searched a lot and tried different things to fix the problem, but nothing is seeming to work.  It's so weird though cause it had been working and now nothing I do is making it work.

Any help?

---

### Post by flipper T on 2011-08-14
in ff install and run flash aid extension

choose the 32 bit version, not the beta

this should fix chrome at same time

---

### Post by gahyoujerk on 2011-08-14
sadly, this did not work.

---

### Post by Actonix on 2011-08-14
One thing that did help me sort out some Flash problems was Bleach which is akin to ccleaner in windows but does require you to make selections where ccleaner works out of the box - I do not recall all the selections I made but I would say install it and run it without administrative rights just so it does not go as deep into the clean and that way you can more or less safely choose all of the options - it does take it's time to run but in the latter stages, ie when it starts it's disk wipe to clean up deleted space, you can shut it down - I did find that some flash problems re-occurred and I had to run it after watching one movie before I could watch another and I eventually worked out the particular selections that worked in order to save having to go through the whole process so with a bit of intuition aiding you I think you should be able to do the same too - best of luck - and do try to report back here so others know what might help in similar situations

---

### Post by gahyoujerk on 2011-08-14
this did not work either.
but  i have noticed i keep getting dependency errors anytime i install sometime.
It will say the installation or removal of this package could not be completed.
Errors were encountered while processing: 
 language-pack-gnome-en-base 
 gconf2 
 compiz-gnome 
 compiz-plugins-main 
 compiz 
 evince 
 gdm 
 light-themes 
 nautilus-data 
 nautilus 
 unity


even though it says the installation could not be completed, the programs still seem to work.  all except flash plugin.
i can't figure out how to fix the dependency errors either.  i tried sudo apt-get update && sudo apt-get dist-upgrade.  
update works, it throws the errors on upgrade though.

---

### Post by gahyoujerk on 2011-08-15
Anyone have any ideas to get the flash working again

---

### Post by aeronutt on 2011-08-15
There was just an update to adobe flash, something about some dependencies added so it wouldn't take up 100% cpu. 

Have you checked updates today?

---

### Post by Actonix on 2011-08-15
From what you say I can only conclude that your problems here lie deeper than just Flash and really the easiest solution would be a reinstall of your OS - obviously backup any important files if you are going down this route.

I'm not familiar with your setup ie Dual Boot OS's and such like but you might want to consider a full wipe if all you have installed is Ubuntu - alternatively you could search the forum for solutions used by others in similar situations, I am pretty sure you would not be the first to be in your position

---

### Post by hubertofliege on 2011-08-23
I'm having the same issue, and it seems strange that we would both encounter it when there was no such problem before.  I think there is something incompatible in the update.  Can I reinstall the previous version?

---

### Post by gahyoujerk on 2011-08-31
Actually I messed up a little bit.  I run Ubuntu off an external hard drive with 2 partitions.  The biggest partition is devoted to Ubuntu and the smallest is NTFS for music and videos I dont want to take on space on my windows but still want to access from windows to listen to the music or watch the videos.

I was having the problem with Ubuntu on my external hard drive, I don't use the dual-boot setup much anymore.

Actually just realized Flash is working on my other Ubuntu, just not I the one I want it to work on.

---

