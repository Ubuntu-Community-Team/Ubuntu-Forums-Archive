---
title: "Gwibber not updating"
date: 2010-06-16
forum: General Help
---

### Post by BrynJones on 2010-06-16
Hi,

Gwibber has stopped updating my facebook stream, does anyone have any idea what might cause this or how to fix?.

Thanks

---

### Post by BrynJones on 2010-06-16
bryn@Compaq-laptop:~$ gwibber

** (gwibber:31492): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:31492): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:31492): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
/usr/bin/gwibber:68: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main()

** (gwibber:31492): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

---

### Post by jivimberg on 2010-06-16
Having the same problem. 
At random times it refresh, and then stop working for hours. 
I've tried many things already (setting language to English - Worldwide, remove and add again facebook account on gwibber) but nothing seams us to work.
Twitter is working fine.

Any idea? 
no facebook refreshing makes Gwibber pretty worthless

---

### Post by tendonstrength on 2010-06-16
FYI, there is another thread going about this topic. No answers, but there is a link to the gwibber bug report. Let us know if you guys find anything else out:

[http://ubuntuforums.org/showthread.php?t=1507319](http://ubuntuforums.org/showthread.php?t=1507319)

---

### Post by BrynJones on 2010-06-17
Deleted account and put back in and it updated...... dodgy!!!!!!!!!

---

### Post by ctxanadu on 2010-07-14
Possibly a facebook authentication issue. I had also faced this.
Delete the facebook account from gwibber,add the facebook account, and during facebook authentication tick the "keep me logged in gwibber". I hope this should resolve the issue.

Thanks

---

