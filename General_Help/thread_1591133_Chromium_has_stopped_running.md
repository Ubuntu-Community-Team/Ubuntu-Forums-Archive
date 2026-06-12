---
title: "Chromium has stopped running"
date: 2010-10-08
forum: General Help
---

### Post by thered on 2010-10-08
Not sure what's happened here, I can only put it down to one of the daily updates.

Chromium has stopped running, it starts, flashes on the screen and shuts down.  I haven't done or changed anything as far as I know.

I've unistalled it completely using Synaptic and reinstalled but no go.

Any ideas?

---

### Post by holiday on 2010-10-08
> **thered said:**
> Not sure what's happened here, I can only put it down to one of the daily updates.

Chromium has stopped running, it starts, flashes on the screen and shuts down.  I haven't done or changed anything as far as I know.

I've unistalled it completely using Synaptic and reinstalled but no go.

Any ideas?

$ dmesg

Anything in there? 

Or try running it from the terminal. I often find messages that the GUI ignores.

---

### Post by markh789 on 2010-10-08
Try removing the Chromium configuration files (i'm not to sure where they are).

Google Chrome, if that's what you mean, would be somewhere under ~/.google or ~/.chrome

But I'm not to sure about Chromium.

---

### Post by thered on 2010-10-09
All I can think of is the last update from the PPA was corrupt.


I've 'forced' and update and it's running OK :o:

@holiday: For future reference, what should I be looking for when I run dmesg? I did run it before and after the fix but could see anything for chrome/chromium

---

