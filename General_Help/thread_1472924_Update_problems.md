---
title: "Update problems"
date: 2010-05-04
forum: General Help
---

### Post by danielsk on 2010-05-04
I installed 10.04 and after messing up when using gparted I had to re-install everything from scratch.

Now I can't get the updates, my system can't reach or pass the public key to most repos.

Is there a problem in the repositories right now, or is there somewhere to reset the Update manager, or something like that?

I have a disk partition with 'home' and another for '/' and I really don't want to mess with the home partition right now (back up is far far away).

---

### Post by quixote on 2010-05-05
I don't think there's anything wrong with the repos.  When you say "can't get the updates" are they also unavailable if you manually hit the button to check for them?  Inability to get the keys, while annoying, should lead only to warning messages.  You should still be able to download those updates. 

All of these are root functions, so it shouldn't have anything to do with your home partition in any case.

One thing you could try is to download from another server than whatever you're using.  Go to System > Administration > Software Sources, and under the "Ubuntu Software" tab, click on the dropdown menu next to "Download from:".  You can have the system scan for the fastest server, or select one at random, or switch to the main server for the whole planet, which had better be up!

---

