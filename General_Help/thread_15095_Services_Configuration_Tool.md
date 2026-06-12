---
title: "Services Configuration Tool"
date: 2005-02-11
forum: General Help
---

### Post by ubuntunewbie on 2005-02-11
Does Ubuntu have a graphical services configuration tool like the one Red Hat has? Or for that matter like the one Windows has (Control panel/Admin Tools/Services). I hate to do chmod -x for entries in init.d for services that I do not want to start while booting my workstation.

---

### Post by evangelion on 2005-02-11
There's a great tool called "services-admin" in the gnome-system-tools package (that is already on your system) that does exactly what you want,  but unfortunately it was taken out of the package due to bugs (or so I hear), so you really don't have it. Keep it in mind for when the bugs get fixed though.  In the mean time,  **rcconf** is as simple as they come, but it's curses based so you run it in a terminal.   I find that it doesn't show all of the services all the time though,  so in case you miss something **sysv-rc-conf** lets you control everything,  it's also curses based.  Both are quicker than chmod -x or updatet-rc.d -f remove'ing though.

---

