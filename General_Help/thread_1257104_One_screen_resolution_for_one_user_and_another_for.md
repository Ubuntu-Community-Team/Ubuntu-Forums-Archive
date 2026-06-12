---
title: "One screen resolution for one user and another for all others andGDM login screen."
date: 2009-09-03
forum: General Help
---

### Post by Darael on 2009-09-03
As per the title really - I've recently changed monitors, and when I first plugged in the new one it was at 1024x768.  Because I'm used to a much higher resolution, I used the NVidia Xserver settings app (run with gksu, naturally) to set it to 1440x1050 and save it to xorg.conf.  I used a clean xorg.conf (unchecked the "merge with existing file" box) just in case.  After a reboot, my screen resolution was at 1440x1050 for GDM and all users except my own, which had reverted to 1024x768.  I have managed to increase this to 1200x900 by using the system->preferences->display app (saying I'd use it despite the warning), but the desired resolution is not available here either, and I would really rather continue to use 1440x1050.

I have checked the contents of my xorg.conf, but it's still set to the resolution I specified - somehow, the resolution is set differently for my user only.

Just in case the information is required, I'm using Jaunty on the amd64 architecture.

Graphics card: Geforce 8800GS using the recommended proprietary driver.

---

### Post by CatKiller on 2009-09-03
Per-user resolution settings are stored in ~/.config/monitors.xml. Delete or rename this file for the problematic user and you'll go back to defaults.

---

### Post by Darael on 2009-09-04
[QUOTE=CatKiller]Per-user resolution settings are stored in ~/.config/monitors.xml. Delete or rename this file for the problematic user and you'll go back to defaults.[/QUOTE]
Wow, that was incredibly simple.  I've renamed the file and will check if it works, but even if not that's a very useful thing to know.

Thank you very much.

  UPDATE:Problem solved.  Thanks again.

---

### Post by tplevrak on 2012-08-25
Thanks very much from me also, this thread solved my same problem too.

___________________________________________
ubuntu 12.04/AMD A8/ATI Proprietary Driver

---

