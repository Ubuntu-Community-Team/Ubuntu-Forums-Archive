---
title: "Can't adjust date &amp; time - need root privs"
date: 2010-03-06
forum: General Help
---

### Post by negativ on 2010-03-06
Note this is KDE on Karmic.

Trying to enable ntp by setting "Set Date & Time Automatically" in the KDE clock widget.  When I click Apply, it says "You are not allowed to save the configuration."

The help file says:

> As these settings do not only affect you as a user, but rather the whole system, you must have system administrator (root) access to change the system date and time. If you do not have this access level, this module will only show you the current settings, but your changes will not be saved.

Fair enough, but since I'm never presented with a kdesudo prompt, and you I can't log into KDE as root, what's the fix for this?  Googling has been useless so far.

---

### Post by lidex on 2010-03-06
Looks like you may need a workaround. Have a look here:
[http://ubuntuforums.org/showthread.php?t=775540]("http://ubuntuforums.org/showthread.php?t=775540")

---

### Post by walmartshopper67 on 2010-03-17
I'm stuck with the same problem, the workaround in that thread doesn't work in Kubuntu Karmic (at least for me) as the package referred to (kcontrol) is not available (at least in my installation, which is as up to date as i know how). There has to be a way somehow, otherwise why are these settings there if they cannot be changed?

---

### Post by lidex on 2010-03-17
The general tab in "system settings"?:
```
systemsettings &
```

---

### Post by crayshort on 2010-07-09
So you can do:

```
kdesudo systemsettings &
``` 

After entering your password, click on **Date & Time **under **Computer Administration** and you should be able to change the date and time and save your changes by clicking **Apply**.

---

