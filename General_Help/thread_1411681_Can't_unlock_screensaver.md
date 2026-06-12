---
title: "Can't unlock screensaver?"
date: 2010-02-20
forum: General Help
---

### Post by wkearney99 on 2010-02-20
Using karmic on x64 as an upgrade from jaunty.

I've tried using both the screensaver preferences panel and the gconf-editor and it WILL NOT remove the lock from the screensaver.  When I try using the preferences it does deselect the lock, but comes back again when I reopen the panel.

When I use gconf-editor (as the user, with or without gksu) I get an error that the key is not writable.  Obviously I can't edit it as root, as the UI specifically prevents root from even selecting the lock.

WTF?

Is there some sort of global policy it's depending upon to prevent me from being able to remove the lock option from the screensaver?  If so, where?  

I just want to be able to wake up the eff'ing screen and not have to enter a password.

---

### Post by wkearney99 on 2010-02-21
There is a policy, of sorts.  Use gconf-editor and create a new Default and a new Mandatory screen.  Those will reveal what settings are configured for default and mandatory values.  Inexplicably the screensaver lock is in the mandatory settings.  Remove than and the screensaver panel will properly allow disabling it.

This still leaves a bug in the screensaver panel in that it won't deselect the checkbox for locking the screen when a mandatory value has been set.  The behavior for doing so already exists, in that the root user is prevented from being able to set it.

---

