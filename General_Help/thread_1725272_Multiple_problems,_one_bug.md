---
title: "Multiple problems, one bug?"
date: 2011-04-09
forum: General Help
---

### Post by Robing Goodfellow on 2011-04-09
Not sure if this is a bug, if it is, if its a Ubuntu bug or a Mozilla bug, or?????? so I'm putting it here to seek guidance.

I'm running Maverick 64 on a 64 bit HP G62 Laptop with Firefox 4.0.

I'm still new at this so I may have done something a bit foolish without knowing it.

Everything worked fine yesterday.

Things were VERY slow today on my machine, not on my wife's (same machine, Windows 7, through the same wifi router on a cable modem).  This is what happened:

I've been running Banshee 1.8, wanted to upgrade to the new 2.0, been waiting for the ppa.  Found it this morning.  I ran:

```

**sudo apt-add-repository ppa:banshee-team/banshee-daily**
  **sudo apt-get update**
  **sudo apt-get upgrade**
  **sudo apt-get dist-upgrade**

```

During the upgrade line, everything in terminal stopped, then started back up again.  Banshee did not update.

Realized I had some updates that required the machine to be restarted (how in the world did I miss that??), so restarted the machine.  Not slow at first, then slow.  Redid the above code, everything went fine, but Thunderbird and Firefox also upgraded, FF to 4.2 (didn't want that, but have it now ;) )

Some websites take forever to load, some don't, for example, the mozilla sites take forever.  Some of the facebook sites, same, gmail: hit and miss, so I originally thought it was a FF bug, but that should have nothing to do with updates and such through the terminal, right?

Any ideas?  

I tried reinstalling FF 4.0, no joy.

Tried to report a couple bugs in 4.2, but its like my internet connection is stop and start.  My wife's is still working fine, again, through the same router and cable modem.

This is way too painful to live with, but I can't identify the root problem so can't make attempts to fix it.

Any ideas?

regards, Richard

---

