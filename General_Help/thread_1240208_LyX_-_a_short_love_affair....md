---
title: "LyX - a short love affair..."
date: 2009-08-14
forum: General Help
---

### Post by longtom on 2009-08-14
Hi,

I started LyX once and it worked just fine...well...all I did was reading in the help section.

When I tried to restart it I just get a short flash and otherwise nothing.

When I start in Terminal I get:

```

QPaintEngine::setSystemClip: Should not be changed while engine is active
QPaintEngine::setSystemClip: Should not be changed while engine is active
QWidgetPrivate::beginSharedPainter: Painter is already active

lyx: SIGSEGV signal caught
Sorry, you have found a bug in LyX. Please read the bug-reporting instructions in Help->Introduction and send us a bug report, if necessary. Thanks !
Bye.
Aborted

```

Apart from the fact that I can't get to the Help>Introduction for the bug report...any other ideas?

---

### Post by renebs on 2009-08-14
Try to install the latest version from their website, and not the one on the repos.

---

### Post by longtom on 2009-08-15
> **renebs said:**
> Try to install the latest version from their website, and not the one on the repos.

Thank you.

That appeared to have done the trick.  The programm starts.  If it works I don't know since I don't know how it works yet.

However - there is a bug report out there.  I installed a newer Version 1.6.1 from the backports, which appears to be the only way to do so.  No deb files on the LyX site.

So I uninstalled LyX and LyX-common with synaptic.  Than I visted the backports site:

For Hardy it would be this site:
[http://packages.ubuntu.com/hardy-backports/editors/lyx](http://packages.ubuntu.com/hardy-backports/editors/lyx)

Downloaded LyX and LyX-common.  First installed LyX-common and then LyX.  That was it.

If any more problems appear I'll shout.

---

