---
title: "Weather applet does not show Australian forecasts"
date: 2010-12-03
forum: General Help
---

### Post by dcstar on 2010-12-03
There is a problem in the current version of the Gnome weather applet in that the web address it gets the details for a lot of Australian locations is no longer valid.

This is detailed in this bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=628750](https://bugzilla.gnome.org/show_bug.cgi?id=628750) and there is a patch for the source code for **libgweather** which now fixes it in the bug report.

Be warned that you have to currently compile your own fix and I found that the compilation process I used actually put the fixed library files in the wrong location - I had to manually move them to fix the issue (see the bug report for details).

---

### Post by Rodney9 on 2010-12-03
I hope someone releases an easy fix for this.

---

