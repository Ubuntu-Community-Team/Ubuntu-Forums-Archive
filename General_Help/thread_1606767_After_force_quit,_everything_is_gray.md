---
title: "After force quit, everything is gray"
date: 2010-10-26
forum: General Help
---

### Post by daqron on 2010-10-26
Hi everyone. I recently installed 10.04.1 64-bit, and I'm seeing an issue I've never seen before:

Sometimes an app turns gray and stops responding. No problem; it happens. But when I force quit the app, some of my other applications turn gray as well, even though they continue to work without any problems.

This graying of non-stalled apps seems to always affect AWN (avant-window-navigator) and any open terminal windows. Only logging out/in or reboot resets everything. If I kill awn, for example, it is still gray when I start it again.

Any ideas? Not a show-stopper, but pretty annoying.

Cheers,
Jeremy

---

### Post by daqron on 2010-10-26
OK I figured it out. It's a compiz problem. For posterity, the solution is:

Alt+F2
compiz --replace

-- Jeremy
(nothing to see here, just talking amongst myself)

**EDIT:** Posted complete description of the bug here: [http://forum.compiz.org/viewtopic.php?f=86&t=13849](http://forum.compiz.org/viewtopic.php?f=86&t=13849)

---

### Post by kerry_s on 2010-10-27
i think it was after an update compiz started acting up. i been using metacity composting since.

---

