---
title: "Gnome-do Tracker (search) plugin not working"
date: 2010-09-14
forum: General Help
---

### Post by gdebat on 2010-09-14
Title explains it all. The tracker plugin is enabled and it shows up in do's action list but when I try to search nothing happens... no windows, no errors, just a big silent nothing.

gnome-do version : 0.8.3.1 (latest)
gnome-do-plugins version : 0.8.2.1 (latest)
tracker version : 0.8.17 (latest stable)

Does anyone else have the same problem (and preferably a solution as well ;))?

Note: I'm using Lucid.

---

### Post by epirsch on 2010-09-15
I have the same issue on Maverick.

0.8.3.1+dfsg-1ubuntu1 (gnome-do)
0.8.2.1+dfsg-2ubuntu1 (gnome-do-plugins)
0.8.17-0ubuntu1 (tracker)

---

### Post by bbdimitriu on 2010-10-25
Same versions, same problem on Maverick. Have you guys found a solution?

---

### Post by gdebat on 2010-10-26
No solution here yet... In fact I gave up a while ago and am sticking with the gnome search tool. It might be slower since there is no indexing involved however I know I can rely on it. In the meantime I've also tried beagle but was disappointed for the fact that it was not showing all results and the result categorization is crappy compared to tracker.

---

### Post by Tec5nical on 2011-04-19
Yes, unfortunately I exactly have the same issue.

---

### Post by gdebat on 2011-04-20
Bad news : apparently Gnome-Do is not being maintained anymore so we can stop hoping that the tracker plugin will be fixed anytime soon...
BUT
Good news : Kupfer (a very close clone of Do - UI-wise) does support tracker! It's not as nice or polished as Do or Synapse but it is moving in the right direction. There are two tracker plugins, make sure that you enable the one matching your tracker version. Give it a try and see what you think about it.

```
sudo add-apt-repository ppa:kupfer-team/ppa
sudo apt-get update
sudo apt-get install kupfer
```

---

### Post by OttifantSir on 2011-11-05
This is apparently not the case. Do is maintained, and daily builds are available in PPA. Latest stable is still from June 2009, but at the time of writing this, a new build has been initiated 5 minutes ago at [https://launchpad.net/~do-testers/+archive/ppa](https://launchpad.net/~do-testers/+archive/ppa)

Not sure if it fixes the Tracker plugin yet, as I just discovered this, but Gnome Do is being maintained.

---

