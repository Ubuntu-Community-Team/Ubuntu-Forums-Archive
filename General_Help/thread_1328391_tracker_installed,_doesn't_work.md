---
title: "tracker installed, doesn't work?"
date: 2009-11-16
forum: General Help
---

### Post by touchlikefire on 2009-11-16
I installed tracker from the repos, and that was successful.  However, using the GUI (tracker-search-tool) successfully opens, but returns "no results" no matter what my search term is.

Interestingly, there are NO configuration options in the GUI, not even a menu bar -- and I would have thought you'd be able to tell it what folders to index.  Bringing up the log from **/usr/share/tracker/trackerd-log** is empty.

Searching from the command line returns 0 results as well.

**trackerd** and **tracker-indexer** are both running, but using 0 cpu.

Anybody know what is going on?

---

### Post by yopnono on 2009-11-16
> **touchlikefire said:**
> I installed tracker from the repos, and that was successful.  However, using the GUI (tracker-search-tool) successfully opens, but returns "no results" no matter what my search term is.

Interestingly, there are NO configuration options in the GUI, not even a menu bar -- and I would have thought you'd be able to tell it what folders to index.  Bringing up the log from **/usr/share/tracker/trackerd-log** is empty.

Searching from the command line returns 0 results as well.

**trackerd** and **tracker-indexer** are both running, but using 0 cpu.

Anybody know what is going on?

Is tracker still alive? Humm interesting have never had any success with it before.

---

### Post by touchlikefire on 2009-11-16
Tracker is in version 0.6.9 whereas Beagle is in version 0.3.9. I've used both before with different versions of Ubuntu (and am surprised they've stopped including it by default).  Currently my desktop uses Beagle, but I'm just not impressed with it.

Also, Beagle is written in managed code, whereas Tracker is written in native C, so it's inherently faster.  Lastly, Tracker's dev team seems to be more active, and the platform seems to show more promise.

That being said, it's not doing me any good if Tracker won't even work.  This is particularly strange, because I haven't had something compile/install and then not work at all.

---

### Post by touchlikefire on 2009-11-16
Well, aside from being non-obvious, I feel pretty stupid about the solution to this problem.

For whatever reason, tracker indexing isn't enabled by default with the 0.6.95 ubuntu package (nor is the default list of exclusions) so you have to enable yourself.  To do so, you either go to System > Preferences > Search and indexing, or, directly from the [Tracker Homepage]("http://projects.gnome.org/tracker/documentation.html#applications") in a terminal: ```
tracker-preferences
```

---

