---
title: "Text only mode doesn't work"
date: 2006-02-25
forum: General Help
---

### Post by schenkin on 2006-02-25
That probably isn't what its called, but when I try to exit out of x11 my monitor says "Signal out of sync," which i'm guessing means it is getting either the wrong resolution, color depth, or refresh rate. It is a bit of a pain since when something goes wrong I have to blindly type in sudo shutdown -r -t secs "now" :) Any suggestions?

---

### Post by gruepig on 2006-02-26
This doesn't actually answer your question, but "sudo halt" will also perform a shutdown.  Even easier, ctrl-alt-delete should be bound to a clean shutdown. 

As for the signal out of sync, try fiddling with your monitor.

---

### Post by schenkin on 2006-02-26
Those are certainly useful, but what do I do to fix problems if I cannot start X11? Its not the monitor beause the problem didn't start until after I installed new ATI drivers, which work perfectly in X11, but not in console mode.

---

### Post by schenkin on 2006-02-26
It looks like this started when I installed the new ATI drivers.

---

### Post by FlakJacket on 2006-02-26
So why can't you use an emulated console?

---

### Post by schenkin on 2006-02-27
I can, but thats not the point is it? What if something goes wrong? I'd just to get this fixed when I DON'T need it, since it'll be impossible to do when I do.

---

### Post by gruepig on 2006-03-01
You should be able to start X.  Run 'startx'.  Or, to start gdm, 'sudo /etc/init.d/gdm start'.  Or, to start kdm, 'sudo /etc/init.d/kdm start'.

---

