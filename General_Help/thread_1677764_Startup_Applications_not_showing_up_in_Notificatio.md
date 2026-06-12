---
title: "Startup Applications not showing up in Notification Area"
date: 2011-01-29
forum: General Help
---

### Post by VII on 2011-01-29
Hi,

As the titles says, applications enabled under "Startup Applications" does not show up in the "Notification Area". I can see that the processes are running, like update-notifier and xchat for example, but they have now icon representing them. I don't think I've ever seen an "There are updates available"-icon since I installed 10.10.

Help?


Edit: I didn't have any pending updates, so that explains why the update-notification icon's been missing.

Edit 2:
Regarding the xchat icon my guess is it's simply loading before the Notification Area applet has, any known way around this?

---

### Post by sikander3786 on 2011-01-29
Are you sure that Notification Area is there in your panel at least? Or you may have removed that accidently.

You can re-confirm by right clicking the panel > Add to Panel > Notification Area.

---

### Post by ajgreeny on 2011-01-29
I can't help with xchat, but the update notifier does not work that way now, unless you set it to do so.  The default is that the update manager will start as a minimised application, and no notification icon will appear.

If you want to icon again use gconf-editor ->apps ->update-notifier and untick the auto_launch box, as in my screenshot.  I run my system that way as it annoyed me intensely to have the update-manager running in the background with no input from me.

---

### Post by steve oates on 2011-03-07
When I do gconf-editor ->apps ->update-notifier it displays no values at all ? Should I add the ones you show manually.

---

### Post by Habitual on 2011-03-07
No, don't add anything there.

---

