---
title: "how can i make cpu freq changing effect all processors?"
date: 2010-04-22
forum: General Help
---

### Post by uschxc on 2010-04-22
i recently purchased an i7 laptop and really don't want 8 cores on my bar.  i remember there being a file that controlled this but i believe it wasn't writeable.

---

### Post by lukeiamyourfather on 2010-04-22
If you're referring to the GNOME panel applet, I think it changes the speed of all the cores by default. Not sure what text file you're talking about but if it won't let you edit the file its probably owned by root, in which case you'd need to use the sudo command to edit it.

```
sudo gedit
```

That for example would open Gedit with root permissions. Cheers!

---

### Post by QIII on 2010-04-22
Actually, you have to go to each core individually (core0 - core3 for a 4x) and set the scaling for each if you are using the panel applet.  You should be able to move between processors using only a single panel applet.

If you are concerned about the number shown on the process manager, hunt around for the preferences (sorry, not at my machine) and you can have it display a single composite.

Not sure exactly how that will work with the i7's dual threading (which makes the 4 look like 8 )

---

### Post by uschxc on 2010-04-22
that changed by default a long time ago.  that or you have changed your applet to not just display cpu0 over and over.  the file sat under /sys/devices/system/cpu/cpufreq but seems to be gone now.  when i said the file wasn't writable i meant root couldn't write to it either, obviously.

---

### Post by QIII on 2010-04-22
Likely a file in /etc/init.d now.

---

