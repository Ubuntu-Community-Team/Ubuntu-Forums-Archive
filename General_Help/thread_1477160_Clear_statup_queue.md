---
title: "Clear statup queue?"
date: 2010-05-08
forum: General Help
---

### Post by harty83 on 2010-05-08
I have a couple apps that I cannot figure out how to prevent them from starting automatically upon logging in.  They are NOT listed in my Startup Applications under preferences.  For example, pidgin. Pidgin automatically starts at each login even though it is not in the startup apps nor can I find an option in pidgin itself.  Tomboy is another.  I always get an error that tomboy cannot be added to my panel when I restart.  The error in the tomboy panel log is that tomboy is already running.  

Does ubuntu have a hidden "start up" folder like Windows does in the start menu?  Where can I clear this file/folder?

Thanks,
Alan

---

### Post by harty83 on 2010-05-16
Bump.  Anybody?  Quite annoying this is.

Thanks!
Alan

---

### Post by drs305 on 2010-05-16
Sometimes programs that were in the Startup folder are just stubborn!

Try closing all your apps. Then go to System, Preferences, Startup Applications. Select the Options tab and then "Remember...". Do this even though nothing should be running.

Then reboot, go back to the same tab, and untick "Remember ...". This method has worked for at least a few apps that refused to remain closed, including Pidgin.

Added: If you haven't looked, a user's autostart entries are listed in ~/.config/autostart

---

### Post by harty83 on 2010-05-20
> **drs305 said:**
> Sometimes programs that were in the Startup folder are just stubborn!

Try closing all your apps. Then go to System, Preferences, Startup Applications. Select the Options tab and then "Remember...". Do this even though nothing should be running.

Then reboot, go back to the same tab, and untick "Remember ...". This method has worked for at least a few apps that refused to remain closed, including Pidgin.

Added: If you haven't looked, a user's autostart entries are listed in ~/.config/autostart

This worked.  Thanks!!

Alan

---

