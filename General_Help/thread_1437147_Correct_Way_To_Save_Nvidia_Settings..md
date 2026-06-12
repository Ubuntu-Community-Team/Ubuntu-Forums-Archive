---
title: "Correct Way To Save Nvidia Settings."
date: 2010-03-23
forum: General Help
---

### Post by soryu on 2010-03-23
How Do I Save The Settings?
I Changed Them But The Don't Save Every Time I Start Up My PC I Have To Type 
nvidia-settings In A Terminal Then They Apply.

---

### Post by pbrane on 2010-03-23
Have a look at this thread
[http://ubuntuforums.org/showthread.php?t=1416011]("http://ubuntuforums.org/showthread.php?t=1416011")
Basically you need to save the settings in nvidia-settings Configuration. If you hover the mouse over the "Save Current Configuration" button a tooltip will explain. Also *man nvidia-settings* and look in the User Guide->Loading Settings Automatically section.

---

### Post by bodhi.zazen on 2010-03-23
> **soryu said:**
> How Do I Save The Settings?
I Changed Them But The Don't Save Every Time I Start Up My PC I Have To Type 
nvidia-settings In A Terminal Then They Apply.

You have to run nvidia-settings as root

```
gksu nvidia-settings
```

Then your changes will be saved.

---

### Post by soryu on 2010-03-23
Looks Like I Had To Add NVIDIA Settings To Start Up, Thanks. :D

(nvidia-settings --load-config-only) Startup Command.

---

