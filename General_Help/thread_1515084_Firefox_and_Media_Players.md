---
title: "Firefox and Media Players"
date: 2010-06-21
forum: General Help
---

### Post by OrionXIII on 2010-06-21
I love Ubuntu and Firefox - incredibly stable. My only difficulty right now lies in attempting to get media players to work.

SOME Flash animations work (I have the latest Adobe flash player installed).

YouTube sometimes plays, but usually doesn't.
Most TV or News websites media players do not work.
SouthPark Studios does not work - it has the little 'Download Flash Player' icon, I click on it and am told I already have it installed....

I realize this is pretty minimal information, but I'm so uncertain where the issue lays that I'm not sure what info to provide....

I'm running Jaunty Jackalope with all the latest updates.

I've got Firefox 3.0.19 with FlashBlock, NoScript, and AdBlock Plus all installed, but even when I unblock everything, I get the same responses...

Can anyone provide me with any direction or tell me what info I might provide that would help?

Thanks in advance!

Orion

---

### Post by lovinglinux on 2010-06-22
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

