---
title: "Python 3.2 question"
date: 2012-05-24
forum: General Help
---

### Post by smikesmith on 2012-05-24
I've build a relatively simple Python-Gtk3 app that runs on either Python 2.7 or Python 3.2 (I installed Python 3 from repo).  It works correctly with Py2, but with Py3, a Gtk.DrawingArea does not get a Draw signal.  There are no errors or warnings, it just does not call the callback when a ".queue_draw" is emitted.

I'm new at Python and Gtk, but as far as I can tell, it's installed properly.  Since everything else works correctly (buttons, entry boxes, etc.), and since there is no error or warning message at the console (also, diagnostic print() calls embedded in the callback, etc., indicate the callback never happens), I wonder if there's a bug in the gi.repository, or if there's something else I need do?

A friend with a slightly newer Python installation can run my app with no problem...

Thanks, mike

---

