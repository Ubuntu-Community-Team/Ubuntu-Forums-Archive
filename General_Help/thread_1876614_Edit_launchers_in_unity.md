---
title: "Edit launchers in unity?"
date: 2011-11-06
forum: General Help
---

### Post by ELD on 2011-11-06
Okay guys i need to run a command "optirun" before all games, how can i edit the launchers in unity (when you select say games and click a launcher) ?

---

### Post by Gillingham on 2011-11-06
The launcher (and dash application lens) get the data from the .desktop file, so you will need to change the command in that.  These files generally live in ```
/usr/share/applications
``` although some (like chrome) may be put elsewhere.  However, you don't want to edit this file as it might be over written when you upgrade a package so you want to copy this to:
```
.local/share/applications
```
(You may need to create this directory).  Then you can find the exec line in the file and change it to include the optirun command.  Save this file and make it executable.  

Let me know if you need more help.

---

