---
title: "Where are context menus stored?"
date: 2012-08-07
forum: General Help
---

### Post by Rallg on 2012-08-07
About a week ago, I compiled a program (not part of the distro) and installed it. No problem, but I didn't like the program, so I removed it.

Now I see that it has left behind a context menu item. Whenever I right-click on a file with extension *.icc, I am offered the choice of opening the file in the now-deleted program.

Where is that context menu stored in the file system, so that I can manually remove the obsolete choice?

Of course, it might be in several locations, depending on how the program was installed. But I haven't a clue what kind of file stores the information.

---

### Post by cortman on 2012-08-07
I think you want to delete the relevant .desktop file in /usr/share/applications.

---

### Post by Rallg on 2012-08-07
Thanks. That did it.

---

