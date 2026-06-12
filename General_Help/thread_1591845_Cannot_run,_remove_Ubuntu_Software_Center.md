---
title: "Cannot run, remove Ubuntu Software Center"
date: 2010-10-09
forum: General Help
---

### Post by Rogue_417 on 2010-10-09
Well I have Lucid Linx up and running well for the most part; all I have left to do now is load PlayOnLinux.  But not from the Software Center.  I can open it from the menu, but when I click on any aspect of the active screen it greys out for sixty seconds before finally disappearing.  

Action 1. Thinking to bypass this annoyance I entered sudo apt-get install playonlinux.  No luck - it came back with a bus errordependency tree at zero percent.  Huh?  

Action 2. Thinking to remove / reinstall the Software Center I enter sudo apt-get remove Ubuntu Software Center.  Wouldn't you know it - bus errordependency tree at zero percent.  What?

I'm running a 2 gig Pentium M on a Toshiba Satellite A 105, but I have had issues recently just upgrading to Lucid Lynx - previous installs reporting hard disk failures on multiple bad sectors specifically.  When last I tried loading PlayOnLinux the laptop started crashing, stalling freezing etc.  bad news all around.  So why not try again?  First however this Software Center thing.  Any ideas?

---

### Post by wilee-nilee on 2010-10-09
The software center misses dependencies at times, and playonlinux may be in a repository you haven't enabled. Look in synaptic and also look for any broken packages with the custom filters.

---

### Post by Rogue_417 on 2010-10-10
I would, I would do that except that, when I run Synaptic it too goes grey looking for packages and then finally closes.  So Synaptic and Software Manager are both crappin' out on me.  Are these custom filters available elsewhere than Synaptic?

---

### Post by Rogue_417 on 2010-10-11
It appears I'm also having issues with Apt-Get.  I cannot remove either synaptic, or even a game like sudoku.  *None of my package managers appear to work*.  Each of them generates bus errordependency.. 0% - and greyed out screens besides.  May I please have some diagnostic assistance?

---

