---
title: "gnome-terminal in focus"
date: 2010-03-08
forum: General Help
---

### Post by loki_dre on 2010-03-08
how do I ensure a gnome-terminal is kept in focus?

---

### Post by victor.zamanian on 2010-03-08
You could right-click the title bar and select Always On Top, if that's sufficient. There's also an "Always keep on visible workspace" option which does exactly what it says. :)

---

### Post by loki_dre on 2010-03-08
that does not seem to do it....
What I am trying to do is capture keyborad input even if another program is suddenly opened

also, it would be nice if I could do this from the command prompt

---

### Post by victor.zamanian on 2010-03-09
If you run the configuration editor (gconf-editor), then go to /apps/metacity/general, there is an option called "focus_new_windows". The descriptions of this setting are as follows:

Short description: Control how new windows get focus

Long description: This option provides additional control over how newly created windows get focus. It has two possible values; "smart" applies the user's normal focus mode, and "strict" results in windows started from a terminal not being given focus.

Maybe this might help somewhat.

Regarding doing this from the terminal, I'm not too familiar with the configuration editor's CLI, but I'm sure it can be done.

---

