---
title: "Borked some apps by using PPAs..."
date: 2010-01-11
forum: General Help
---

### Post by docus on 2010-01-11
Hi,

I'm running 9.10 and it's been great for me, until a few days ago...  I added some PPAs, and they seem to have produced some conflicts that I don't know how to fix.

I added PPAs for Midori, Webkit, Epiphany, Mozilla (for Firefox 3.7 and Thunderbird 3), and Banshee.

Now I can't open Midori, Epiphany or (strangely) the Ubuntu Software Center.  

I don't know what has caused the problem, and I don't know how to investigate it to work it out either.

I'd be very grateful if some kind person could give me a run-through of how to investigate the problem, so that I can fix it!

Thanks,
Docus

---

### Post by joeknoodle on 2010-01-11
> **docus said:**
> Hi,

I'm running 9.10 and it's been great for me, until a few days ago...  I added some PPAs, and they seem to have produced some conflicts that I don't know how to fix.

I added PPAs for Midori, Webkit, Epiphany, Mozilla (for Firefox 3.7 and Thunderbird 3), and Banshee.

Now I can't open Midori, Epiphany or (strangely) the Ubuntu Software Center.  

I don't know what has caused the problem, and I don't know how to investigate it to work it out either.

I'd be very grateful if some kind person could give me a run-through of how to investigate the problem, so that I can fix it!

Thanks,
Docus
Try removing the PPAs, then redo them one at a time, verifying each is successful before moving onto the next.

---

### Post by t0p on 2010-01-11
> **joeknoodle said:**
> Try removing the PPAs, then redo them one at a time, verifying each is successful before moving onto the next.

Maybe you should re-read the OP.  your suggestion doesn't address the stated problem.

**OP:** I suggest you revert the apps to the supported versions.  For example: uninstall *Midori* (*sudo apt-get purge midori*); remove the *Midori* PPA from /etc/apt/sources.list; update the package list (*sudo apt-get update*); reinstall *Midori* **from the regular repos**.

If you do this for every application concerned, testing as you go along, hopefully that will fix the problem.

---

### Post by docus on 2010-01-12
Thanks very much, I'll give that a try and then report back!

---

### Post by docus on 2010-01-13
Yay, my system is fixed!  Thanks so much for your helpful advice.

I did it all through Synaptic, and I learnt a lot about adding and removing repos and about downgrading to earlier stable versions of apps.

The problem seems to have been with the Webkit PPA, which didn't play nicely with my particular system configuration.

All in all, it was a simple process of deduction (elementary my dear Watson!)

Now I'll know what to do the next time I bork my system with overzealous upgrades...!

Thanks again :D

---

