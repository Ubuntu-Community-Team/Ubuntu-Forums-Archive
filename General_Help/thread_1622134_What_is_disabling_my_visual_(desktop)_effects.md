---
title: "What is disabling my visual (desktop) effects?"
date: 2010-11-15
forum: General Help
---

### Post by wasteed on 2010-11-15
I've been having this weird problem ever since upgrading to Lucid - which was some months ago now - and wonder if anyone has seen similar behaviour or even knows of a solution.

As I am the sole user of my desktop at work, I always leave the computer on and myself logged in. However, every Monday morning, when I return to work after the weekend, I find that my Visual desktop effects setting has reverted back to "None" from "Extra", so all of my Compiz effects have been disabled, and quite often my cairo-dock has stopped working too.

So, at this point, I have to visit the Appearance Preferences->Visual effects tab and re-enable the effects (which always takes an age as it decides it has to check for a 3D driver, even though it is already installed and in use), then browse through ccsm to turn on the compiz effects once more, and maybe restart cairo-dock.

After doing this, my desktop will be fine - all effects enabled - for the rest of the week, until the following Monday morning when the damn thing is disabled again! This happens every week and is getting quite annoying now. As far as I can remember, it never happened before Lucid.

I've tried saving my session, login out then back in, and even searching to see if a  weekly cron update job is responsible - not that I can see - but it keeps happening. 

And yes, the screensaver locks my screen when I am away, so my office mates  can't be playing tricks on me!

Has anyone else suffered from this sort of problem ?

---

### Post by inso_741 on 2010-11-15
why not add a ```
compiz --replace
``` in start-up

---

### Post by wasteed on 2010-11-15
It's already there.

Besides its not to do with "start-up" as such, as I am already logged-in...

---

