---
title: "volume applet issue"
date: 2011-04-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-04-07
there appears to be an issue with the roll mouse up/down feature on it
the icon show the volume increase/decrease but the master volume is unaffected i know it works on ubnutu like it should
Xubuntu 10.04.2
```
cat /proc/version
Linux version 2.6.32-30-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011
```

---

### Post by EdwardR on 2011-04-07
Try this - 

Right click on the sound icon,
Click "Properties",
Under "Sound card", click on the drop down arrow, click on the other mixer if there is another option shown.
Click on the drop down arrow again and select the original mixer.  (We're just trying to reset the mixer, not change it, that's why we are going back to the original)
Close the mixer plugin window.
Try the scroll wheel over the icon now.

---

### Post by pqwoerituytrueiwoq on 2011-04-07
worked :)

---

### Post by EdwardR on 2011-04-07
Great!

---

