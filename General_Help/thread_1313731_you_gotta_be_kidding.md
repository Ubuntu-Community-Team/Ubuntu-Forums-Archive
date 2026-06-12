---
title: "you gotta be kidding"
date: 2009-11-04
forum: General Help
---

### Post by captkit on 2009-11-04
i know i'm not helping-but-just sp wasted 6 hours trying to get virtualbox running in "jaunty". --fail
several attempts at googlearth --fail  the installers said sucess!  the apps never appeared.  the repositories are full of stuff that doesn't do anything.  ok i know it's free and all and it runs firefox (like it's 1999) but how about some flags or something so we don't waste time on crap that doesn't work.
I hate to say it but ubuntu makes windows(tm) look like it's worth the money.

---

### Post by QIII on 2009-11-04
All three worked for me in Jaunty, even when FF was Shiretoko.

All three run for me in Karmic.  I have FF 3.5.4, which actually updated itself from 3.5.3 without waiting for the Canonical version.

I haven't run into anything that wasted my time by not working.

But that is obviously not how it is working out for you, so it needs to be solved.

Could you pick the most pressing concern and let us see if we can deal with that?  One at a time is easier.

---

### Post by SirBismuth on 2009-11-04
I got all those working in Jaunty, and Virtualbox works fine in Karmic.  Haven't tried Google Earth yet.

Also had no issues with FF, bar a few flash-related crashes so far, that have been fixed.

B

---

### Post by tripleaces on 2009-11-04
Are you sure your installs were bad? I've had a couple programs install and not automatically setup links to them in the menu or desktop. Have you looked at the installation destination?

---

### Post by P4man on 2009-11-04
> **captkit said:**
> i know i'm not helping-but-just sp wasted 6 hours trying to get virtualbox running in "jaunty". --fail
several attempts at googlearth --fail  the installers said sucess!  the apps never appeared.  the repositories are full of stuff that doesn't do anything.  ok i know it's free and all and it runs firefox (like it's 1999) but how about some flags or something so we don't waste time on crap that doesn't work.
I hate to say it but ubuntu makes windows(tm) look like it's worth the money.


Doing a wild guess: you are installing **packages** in synaptic package manager, and not **applications** in add/remove programs or ubuntu software center. You installed the only thing that comes up in synaptic when you search googleearth, but guess what, its not the program. Its a tool that lets you make a package, not google earth istelf as google earth is not in the default repositories. You have to add the [medibunti repositories]("https://help.ubuntu.com/community/Medibuntu") (or fetch it from the google website) as its not opensource.

---

