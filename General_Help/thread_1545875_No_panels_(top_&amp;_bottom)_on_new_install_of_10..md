---
title: "No panels (top &amp; bottom) on new install of 10.04"
date: 2010-08-04
forum: General Help
---

### Post by eugener on 2010-08-04
I installed 10.04 twice on a recycled 10 year old Dell, using both a regular and an alternative live CD.  With both installs, there were no top or bottom Gnome panels when I started up so I could not access the programs, make changes, etc.  A message appeared asking if I wanted to delete the aplets (or panel?) the first time I started it up.  I answered yes with the regular CD and no with the alternative, but did not see the massage again.  Any suggestions welcome.
Gene

---

### Post by WorMzy on 2010-08-04
Try running "gconf-tool-2 --shutdown" then delete ~/.gconf/apps/panel, and then restart.

Do you get any panels then, or do you get the error? Post the error here if you get one.

---

### Post by Smart Viking on 2010-08-04
Hey. Can you right click and do things like create new files? If so try the following:

right click, and select create an empty file, then open it and insert this:

```
#!/bin/bash
gnome-panel
```

Then save it as "panel.sh", then right click on it, go to properties->permissions and then allow it to execute as program, and then double click the file. Hopefully it will launch the panels. :)

---

### Post by celldweller1591 on 2010-08-04
Try right click and add panel, see if it works. If they do, you can set them manually.

---

