---
title: "Software Centre won't quit"
date: 2011-03-05
forum: General Help
---

### Post by watgrad on 2011-03-05
Hi - 
I've got a problem with the software centre.  

When I close this application - the window disappears, but the process continues to run in the background (consuming ~50% of cpu activity).

I've tried apt-get clean, apt-get purge ...etc. to remove any problems - but this behaviour persists.  

Is there a way to find out what is going on?
Thanks for you suggestions...

Maverick, intel core2 quad

---

### Post by TeoBigusGeekus on 2011-03-05
Launch it from terminal
```
software-center
```
to see if you get any error messages when it hangs.

---

### Post by watgrad on 2011-03-05
OK - did that - this is what it said:

2011-03-05 11:44:05,211 - softwarecenter.app - INFO - software-center-agent finished with status 1
/usr/share/software-center/softwarecenter/view/catview_gtk.py:976: GtkWarning: gtk_box_pack: assertion `child->parent == NULL' failed
  self.box.pack_start(self.image, False)
Killed


I had to kill the process again...

---

### Post by watgrad on 2011-03-05
anyone?  anyone?

---

