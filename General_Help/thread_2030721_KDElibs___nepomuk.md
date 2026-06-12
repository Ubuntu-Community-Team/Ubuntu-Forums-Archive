---
title: "KDElibs?   nepomuk?"
date: 2012-07-21
forum: General Help
---

### Post by Subito Piano on 2012-07-21
Hi!  I noticed an application nepomuk in my freshly-installed lubuntu system (12.04).  I don't know if it is part of lubuntu or if it came thru an update that i didn't read thru.  I don't need it and went to uninstall.  It would pull a ton of KDElibs and other KDE apps with it.  What the heck?  I didn't install any KDE apps.  

So - does lubuntu come with all this KDE stuff or is this most likely junk i can jettison?  (I realize i need to take notes on everything if i choose to uninstall - just in case - and not to "completely" uninstall until i KNOW i don't need those apps.

Thanks!

---

### Post by PaulW2U on 2012-07-21
No, neither nepomuk or any of the KDE libraries are initially installed with Lubuntu. They won't have been installed as part of a routine update either.

You must have installed them inadvertently, perhaps you installed an application without realising it relied on the KDE libraries.

Personally, I would do what you have already done and start the uninstall process but take very careful note of what is being uninstalled just in case there is something there that you want to keep. Synaptic will of course tell you exactly what is being removed as you've probably already found out.

---

### Post by BigSilly on 2012-07-21
Odd. I too noticed this last night when updating the missus' laptop running Xubuntu 12.04. The only KDE application she runs is K3b, but I was still very surprised to see so many KDE libs being pulled in as per the OP.

---

### Post by Subito Piano on 2012-07-21
Yeah (PaulW2U) -- that is what i would suspect BUT i saved so many screenshots of the terminal window in Synaptic to know just what was going in -- and none of them show any KDE stuff....so i'm mystified (like BigSilly).  When I have time i'll start uninstalling carefully and post the results.  I suppose the 42 MB or so won't kill me but idk if it's dragging my system resources at all...but it's sure annoying!

---

### Post by PaulW2U on 2012-07-21
> **Subito Piano said:**
> Yeah (PaulW2U) -- that is what i would suspect BUT i saved so many screenshots of the terminal window in Synaptic to know just what was going in -- and none of them show any KDE stuff....so i'm mystified (like BigSilly).  When I have time i'll start uninstalling carefully and post the results.  I suppose the 42 MB or so won't kill me but idk if it's dragging my system resources at all...but it's sure annoying!

The libraries won't get loaded unless you actually run an application that uses them so they won't drain your resources. Obviously if there are any updates you'll get prompted to download them but even if they're all updated, 42MB is not a lot to download these days.

---

### Post by Subito Piano on 2012-07-24
Anyone visiting this thread: [COLOR=Red]**BEWARE!!!**[/COLOR]

Yanking those libs pell-mell (plus one other file i neglected to write down) has cost me over 9 hours labor so far, and i still don't have a solution.   For 150 MB -- "if it ain't broke, don't fix it!"  

Interesting, using synaptic always warns me of additional files to be downloaded with any software, but commandline installation does not always do so. 

Those interested in my woes can check [here]("http://ubuntuforums.org/showthread.php?p=12126957#post12126957"), as it called for a separate post.

yiii............

---

