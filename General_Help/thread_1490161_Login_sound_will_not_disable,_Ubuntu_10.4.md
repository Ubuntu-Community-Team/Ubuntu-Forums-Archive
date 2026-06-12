---
title: "Login sound will not disable, Ubuntu 10.4"
date: 2010-05-21
forum: General Help
---

### Post by Ziphilt on 2010-05-21
I want to disable the login sound, and System->Administration->Login Screen has an option that seems to be relevant. However, it has no effect. I know the file is at [/usr/share/sounds/ubuntu/stereo/desktop-login.ogg]; would I hurt anything by moving it?

I have searched Google and gconf-editor, to no avail.

---

### Post by Ziphilt on 2010-05-22
Solved by unchecking the entry in System->Preferences->Startup Applications. Why didn't that checkbox do anything, though?

---

### Post by Walpy on 2011-03-14
Unchecking the "Play log-in sound" under
> System > Administration > Login Screen
Will cause the "sytem-ready.ogg" to be disabled.

Unchecking the "GNOME Login Sound" under
> System > Preferences > Startup Applications
Causes to disable the "desktop-login.ogg".

Thanks anyway for helping me to find it!

---

