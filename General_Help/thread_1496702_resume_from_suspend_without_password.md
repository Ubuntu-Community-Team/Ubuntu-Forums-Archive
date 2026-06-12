---
title: "resume from suspend without password?"
date: 2010-05-29
forum: General Help
---

### Post by JUSTINBEAIRD on 2010-05-29
in kubuntu how can i resume from suspend without password? it annoys the crap out of me i have been looking all over and cant find anything in settings to do this

---

### Post by Ozymandias_117 on 2010-05-29
Open a terminal and type ```
gconf-editor
```

Navigate to ```
apps/gnome-power-manager/lock
``` and uncheck "suspend"

---

### Post by JUSTINBEAIRD on 2010-05-29
> **Ozymandias_117 said:**
> Open a terminal and type ```
gconf-editor
```

Navigate to ```
apps/gnome-power-manager/lock
``` and uncheck "suspend"

thanks for your help but gconf-editor isnt installed in kubuntu and i still want the computer to suspend but i dont want to unlock it wen it resumes

i took the check mark out of lock screen on resume in "power management" but it still didn't help 

i also tryed editing /etc/default/acpi-support too
# Comment this out to disable screen locking on resume
# LOCK_SCREEN=true

but it is still locking the desktop on resume

---

### Post by Ozymandias_117 on 2010-05-29
Sorry, I wasn't paying enough attention, missed that you were using Kubuntu.

---

