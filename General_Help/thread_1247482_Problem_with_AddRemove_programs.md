---
title: "Problem with Add/Remove programs"
date: 2009-08-23
forum: General Help
---

### Post by geoff4376 on 2009-08-23
When I try to load the Add/Remove Programs app, it won't download the programs, and I get this message : "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E_: cache->open() failed, please report."

When I try to run what it tells me in Terminal, It opens up Frostwire.  I downloaded Frostwire last night, and while I was installing it, the Add/Remove Programs thing started talking about errors, but Frostwire opened up.  I was able to download stuff, but when I closed the Add/Remove app Frostwire closed also.  I'm running Ubuntu 8.04 on a Dell Optiplex gx260 if that helps.  I am a complete n00b at this.  Any help is greatly appreciated.

---

### Post by hal10000 on 2009-08-23
Frostwire should have nothing to do with [COLOR="Red"]dpkg --configure -a[/COLOR]. So, if it starts up, just close it and go on with reconfiguration.

Maybe a better way to get info about broken packages or something like this is to open the [COLOR="Red"]synaptic[/COLOR] Package Manager (From the menu or from a teminal window with the command [COLOR="Red"]sudo synaptic[/COLOR], and then in the synaptic program click to "userdefined Filter" and then to "broken packages", where you can find packages which are not installed correctly. You can then reinstall these packages.

---

