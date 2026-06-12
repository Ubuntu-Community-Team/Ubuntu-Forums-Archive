---
title: "Cannot login from locked screen"
date: 2010-11-04
forum: General Help
---

### Post by jazzgossen on 2010-11-04
I can't log in from a locked screen anymore, such as when returning from sleep or hibernation. I can, however, work around the problem by clicking "switch user" and logging in from the GDM greeting screen. Logging in from a terminal also works.

I recently had a problem where /etc/passwd, /etc/groups and some other files were deleted. But I have restored them - otherwise I couldn't log in at all.

But something must still be missing. What could be causing this problem?

---

### Post by jazzgossen on 2010-11-15
I will log my attempts of fixing the problem here. 

[LIST=1]
[*]Reinstall gnome-screensaver did not help.
[*]Reinstall libpam-modules, libpam-ck-connector, libpam-runtime, libpam-smbpass did not help.
[/LIST]

---

