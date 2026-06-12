---
title: "Run app in background"
date: 2009-12-04
forum: General Help
---

### Post by embryo_ on 2009-12-04
I have added two apps to the autostart at boot in xubuntu. But how can i control which to be on top? Its a slideshow (feh) and a browser (opera). I want Opera to run in background. Now, when i boot, the slideshow starts first, then opera starts and the slideshow is minimized.

---

### Post by jbrown96 on 2009-12-04
Create a new startup entry that runs ```
sleep 3 && opera --remote 'lower()'
``` You may need to change the time it waits before running that command (i.e. make it longer). You may also need to sleep your slideshow for a few seconds, so opera can open, then minimize.

try changing the feh entry to ```
sleep 7 && fed
```

---

