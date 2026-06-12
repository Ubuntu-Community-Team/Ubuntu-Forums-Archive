---
title: "can't disable lock screen when going for suspend"
date: 2011-08-28
forum: General Help
---

### Post by ducttapeandzipties on 2011-08-28
Whether this box is clicked or not, my computer always locks the screen when going into suspend.  Is there maybe a config file that overrides this?

---

### Post by ducttapeandzipties on 2011-08-28
The lock value in .xscreensaver is set to false.  It still locks the screen every time I suspend.

---

### Post by Toz on 2011-08-28
Which version of xubuntu are you using? Have you had a look at: 
Settings->SettingsManager->PowerManager->Extended? There is a "Lock screen when going for suspend/hibernate" option (in 11.04 at least).

---

### Post by ducttapeandzipties on 2011-08-28
> **Toz said:**
> Which version of xubuntu are you using? Have you had a look at: 
Settings->SettingsManager->PowerManager->Extended? There is a "Lock screen when going for suspend/hibernate" option (in 11.04 at least).

sorry 11.04. yes I tried that setting, it has no effect.

---

### Post by Toz on 2011-08-28
Might be a long shot here, but **/etc/default/acpi-support** has a 
> LOCK_SCREEN=true statement (default value is true). According to the information in that file, this statement is deprecated, but you could give it a try and change it to false.

---

