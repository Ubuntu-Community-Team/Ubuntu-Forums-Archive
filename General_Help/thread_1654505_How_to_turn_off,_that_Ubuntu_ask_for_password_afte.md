---
title: "How to turn off, that Ubuntu ask for password after a while?"
date: 2010-12-28
forum: General Help
---

### Post by daGrevis on 2010-12-28
How to turn off, that Ubuntu ask for password after a while? For example, I go away from the computer for 20 minutes, then I come back, but it asks for my password. How to turn it off?

---

### Post by lungten on 2010-12-28
If its the screensaver locking you out after a while of inactivity, ```
System->Preferences->Screensave->Lock screen when screensaver is avtive
```

---

### Post by johncc on 2011-01-13
> **lungten said:**
> If its the screensaver locking you out after a while of inactivity, ```
System->Preferences->Screensave->Lock screen when screensaver is avtive
```

I'm not the OP, but am having a problem with this.  In System/Preferences/Screensaver the "lock screen" is indeed UNchecked, but I am getting the login screen after about 5 minutes of idle.  

It had been behaving properly before, but I had had to uninstall nvidia drivers which led down a path where I uninstalled and reinstalled xserver-xorg.  Now X is working but I can't get rid of the password prompt.  ?

I also did:
```
ALT+F2
Open gconf-editor.
Go to /apps/gnome-power-manager/lock/
Uncheck "Suspend"

```
And after 5 minutes it still went back to the login screen

Thank you,
John

---

