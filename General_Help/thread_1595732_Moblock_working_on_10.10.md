---
title: "Moblock working on 10.10?"
date: 2010-10-13
forum: General Help
---

### Post by Hack.The.Pow. on 2010-10-13
Has anybody here gotten moblock to work on 10.10 yet?

I just upgraded from 10.04 and the update has disabled mobloquer(which I can live with) and blockcontrol.  Moblock still seems to be there but is basically useless without blockcontrol(or is it?).  

Do we just have to wait for a new update for blockcontrol?

---

### Post by jre on 2010-10-15
I will release maverick packages today.

---

### Post by jre on 2010-10-15
I just made new moblock/blockcontrol/mobloquer packages, also for Ubuntu Maverick (10.10). They are built now and will be available soon.

If you don't need a GUI I recommend to move on to pgl (PeerGuardian Linux). That's based on moblock/blockcontrol/nfblock, and has some fixes and improvements. All development efforts go to this new project now. But I can't tell when a GUI will be available.

---

### Post by Hack.The.Pow. on 2010-10-15
Sweetness!! Thanks a lot man.  

A Gui is always nice so i just got mobloquer again for now.  Just Curious but why would you recommend pgl over moblock?

---

### Post by jre on 2010-10-15
Generally pgl is developed, the others not (although as you see, I still support moblock & co). Now we have one project instead of three, which allows a better integration (this already helped greatly for the blocklist management)

pgld
[LIST]
[*]uses less memory than moblock
[*]some bugs fixed
[*]improved logging, including direct logging of ports and protocol of blocked IPs
[/LIST]
pglcmd[LIST]
[*]has seen many minor improvements to blockcontrol
[*]improved blocklist handling, using less disc space, extended range descriptions after merging several ranges
[*]fixed watchdog implementation
[*]direct support of iblocklist blocklists in human readable form (although I backported this to blockcontrol)
[/LIST]

For other distributions
[LIST]
[*](not important for you since you use my Debian packages): easy installation with one Makefile, compared to three sources from different places + patches.
[/LIST]

---

### Post by Hack.The.Pow. on 2010-10-15
Sounds good.  I definitly will check out pgl soon.  

Thanks again for the maverick moblock packages!

---

### Post by jre on 2010-10-16
That reminds me that I should add a script to transition your blockcontrol configuration to the pgl one.
But most variables have the same name, there are just minor changes.

---

### Post by KegHead on 2012-10-09
Hi jre!

I installed moblock on Xubuntu and I'm unable to log onto Google Chrome.

Any ideas?

Is there a mirror for a deb file?

Thanks!

KegHead

---

### Post by lisati on 2012-10-09
A has changed in the 2 years since this thread was last active.

Thread closed.

---

