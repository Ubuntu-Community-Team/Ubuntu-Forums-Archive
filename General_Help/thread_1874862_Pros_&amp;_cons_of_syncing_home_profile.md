---
title: "Pros &amp; cons of syncing home profile"
date: 2011-11-03
forum: General Help
---

### Post by altjx on 2011-11-03
I have a desktop with a 26" monitor and a 15" Dell Laptop.

Is there any big disadvantages to syncing home profile using Ubuntu One? I've been becoming more attached to the service and instead of having to go from one PC to the next to configure settings like Compiz, keyboard shorcuts, etc...

Do anyone think it's a bad idea or is anyone already doing this?

---

### Post by LowSky on 2011-11-03
I wouldn't do it. Mainly because of little idiosyncrasies. 

But why not test it. Back up the data on both systems. then set U1 to sync. See what happens. If it's fine then use it and report back. if not turn off sync, delete the new data and replace with the old.

---

### Post by agillator on 2011-11-04
The above 'test to see what differences there are' is excellent advice. My only comment is using some outside location (Ubuntu One) to store your files. That is probably just my natural caution and paranoia speaking, but I do not trust ANYTHING I don't control with sensitive data. Perhaps I am just an old fogie, but there you have it. If you can have the two computers talk to each other through ssh as I can, then I would highly recommend using rsync to keep them synced. If you proceed a little carefully you can end up with an rsync session that will keep those files synced you want synced and not touch those that should not be. Your command line will be a nightmare most likely, but most anyone can do it if you do it a step at a time. For example, email and browser information is excellent to keep synced. If you have a check register on the computer, that is a good candidate.

---

