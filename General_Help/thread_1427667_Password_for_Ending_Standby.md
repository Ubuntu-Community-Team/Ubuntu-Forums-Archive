---
title: "Password for Ending Standby"
date: 2010-03-11
forum: General Help
---

### Post by nsivin on 2010-03-11
I am running Ubuntu 9.10 on a PC. When the computer is on standby and I want to fire it up again, Ubuntu demands a password. Since the computer is inside a private house, and I never put it on standby unless I am at home, entering a password is an unnecessary nuisance. Is there some way to turn this “feature” off?

---

### Post by ibuclaw on 2010-03-11
Open the application launcher via **Alt + F2** and type in:
```
gconf-editor
```
Browse to the Gnome-Power-Manager application
```
/apps/gnome-power-manager/lock
```
Disable password prompt on Resume from Suspend via unchecking the checkbox next to "suspend".

Regards
Iain

---

### Post by rahilm on 2010-03-11
System->Preferences->Screensaver
uncheck the "Lock screen when screensaver is active"
Click on Power management..
Put "Never" wherever necessary

---

### Post by n0dix on 2010-03-11
Maybe [this]("http://ubuntuforums.org/showthread.php?t=283768") helps you. It's a bit old and i don't tested. I hope works for you.

---

