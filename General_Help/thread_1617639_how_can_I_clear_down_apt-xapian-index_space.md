---
title: "how can I clear down apt-xapian-index space"
date: 2010-11-09
forum: General Help
---

### Post by tstubbs on 2010-11-09
Hi,

My system is giving me a low space on filesystem warning. When I run disk analyser, it seems that /var/lib/apt-xapian-index is using 97% of it!! That's 8.9GB.

I found another post which explained that each time this package runs it builds a new index set, and how to make it only update new packages. I made that change, but this doesn't release the 8.9GB that I guess can just be cleared down somehow...

I hope it can be cleared down anyway... please, can someone tell me how to clear all this down? I do want the package to remain running on the system, I just want to clean it up and release all that space.

btw. I'm on Lucid, I also saw the warning on Jaunty but it went away after upgrade to Lucid... now it's happening again, I can't ignore and hope it goes away for ever! lol

thanks a lot for all help!
tstubbs

---

### Post by tstubbs on 2010-11-12
Please, someone must know the answer to this... can I even just re-install the package? 

(I'm cautious about trying that first because the package is something to do with the synaptic I think, and don't want to mess up the ability to re-install)

thx
tstubbs

---

### Post by knarf on 2010-11-24
> **tstubbs said:**
> Please, someone must know the answer to this... can I even just re-install the package? 

(I'm cautious about trying that first because the package is something to do with the synaptic I think, and don't want to mess up the ability to re-install)

thx
tstubbs
The xapian index is used for the search box in synaptic. If you can live without that functionality you can purge the apt-xapian-index package:
```
sudo apt-get autoremove --purge apt-xapian-index
```...or use synaptic to **purge** (not just remove as you want to get rid of the database as well) that package. You won't have access to the search box anymore (it will say 'no apt-xapian-index found') but synaptic should work as before. If you regularly use the search box you might miss it. If you've never used it I'd say go ahead and purge that package (and python-xapian).

[COLOR=DarkRed]Only do this if you are up to hacking your system. If you feel insecure about removing packages just leave it as it is.[/COLOR]

---

### Post by tstubbs on 2010-11-25
Thank you knarf!

I probably could just purge, I'd rather keep the functionality if I can though.

Is it possible to purge and then re-install the package so that it creates a fresh new index... one that then doesn't take up over 3GB of space?

tstubbs

---

