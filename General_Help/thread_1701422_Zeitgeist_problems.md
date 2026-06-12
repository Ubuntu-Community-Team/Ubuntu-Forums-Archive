---
title: "Zeitgeist problems"
date: 2011-03-06
forum: General Help
---

### Post by nathan28 on 2011-03-06
10.04 64-bit.

Can't seem to get Sezen or Activity Journal to get working properly. I'm trying to update both right now, but am getting hit-or-miss (mostly miss) logging of docs. It looks like if I open something from a Nautilus window, it's logged. Anything else is ignored. I've used the zeitgeist-daemon --restart, and had to turn the machine off a couple times.

~/.recently-used.xbel looks to be working fine, though.

Where should I be looking for problems? I know these are sort of bleeding-edge but it can't be that bleeding. Worked fine three days ago.

---

### Post by Habitual on 2011-03-06
I loved GAJ but had to remove it because it worked one day, but not the next.

Even with the bleeding edge PPA it was borked.

have a look at [http://askubuntu.com/search?q=zeitgeist](http://askubuntu.com/search?q=zeitgeist)

---

### Post by nathan28 on 2011-03-06
Amazing, now files are outright disappearing from the history. Going to uninstall, reboot for the hell of it and try, try, try again with an install from the ppas. hope I don't lose file tags. X(

going to full purge the damn thing when I get home. Remove the PPAs, remove the packages, apt-get remove and then finish it off with the locate/rm death squad.

I think I must have got some conflicts in the installed packages between bleeding edge ppa and the regular repo, probably by mixing CLI ppa kung-fu with hamfisted Synaptic laziness.

I thought I was getting my own personal SkyNet. Instead it was more like getting live journal with intermittent server data losses.

This will be awesome... if it works.

---

### Post by nathan28 on 2011-03-09
Bump.

Did apt-get remove --purge of GAJ, zeitgeist, sezen, and tracker. Searched through synaptic to find related packages and did complete removals of them. Did an autoremove. Then did a locate for activity-journal, GAJ, sezen, tracker and zeitgeist and did an rm on everything that showed up with the exception of stuff that wasn't related (like my .flvs of all the Zeitgeist movies saved for when TPTB hit the internet killswitch (j/k)).

Anyway, did a reinstall of GAJ, zeitgeist and tracker from the PPAs.

Looks good, except I can't tag anything anymore. **TAGGING WAS THE REASON I WENT TO ALL THIS TROUBLE.**

Tracker is .9 from the unstable PPA
GAJ is .5.0.1 iirc
zeitgeist is .7 iirc
sezen is whatever came by default w/ the repos

I don't run Synapse b/c it makes my ATI card cranky and Do learns faster.

Any help on this would be *greatly* appreciated. Even a non-zeitgeist, non-tracker app to tag/search files from the desktop. I'm afraid to install any new zeitgeist reporting packages besides the defaults in the PPAs.


EDIT: From [one of the GAJ devs](http://askubuntu.com/questions/29706/tagging-gone-from-nautilus-gaj-tracker):

[quote]Hi, GAJ maintainer here. Since the last version (0.6) the tagging feature (powered by Tracker) has been removed from GAJ, due to problems and random crashes. For what concerns Nautilus, as far i know, installing Tracker should let you tag out of the box.[quote]

---

