---
title: "Black Screen (Compiz - Opacity, Brightness and Saturation)"
date: 2011-04-12
forum: General Help
---

### Post by ZereoX on 2011-04-12
After Enabeling Opacity, Brightness and Saturation in Compiz, my screen became black and I am unable to see what I'm doing. The Mouse is still visible. Is their an easy way to disable a Compiz Plugin and that I could perform "Blind"?

---

### Post by sanguinoso on 2011-04-12
I think this thread should get you on your way.
[http://ubuntuforums.org/showthread.php?t=640199](http://ubuntuforums.org/showthread.php?t=640199)
You can reboot into a terminal session and edit the configuration files.

---

### Post by stinkeye on 2011-04-12
Your not alone, I've seen a few people do this because when you add a new window
in the **Opacity, Brightness and Saturation** plugin it defaults to %100 transparent
and before you no what you've done all your windows are invisible.

Hit alt+F2
Type in 
```
metacity --replace
```
and press **Enter**


Fix up the plugin in ccsm and run
```
compiz --replace
```

---

### Post by ZereoX on 2011-04-12
Here is the Fix:
Press CTRL+ALT+F1. This will open up a Terminal mode. From their simply log-in and delete the .xml's for the Opacity, Brightness and Saturation located in to disable it:
```
/home/<your username>/.gconf/apps/compiz/plugins/obs/
```

Then restart.

Thanks for the help guys.

---

