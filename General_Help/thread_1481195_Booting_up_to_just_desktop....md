---
title: "Booting up to just desktop..."
date: 2010-05-12
forum: General Help
---

### Post by all4him on 2010-05-12
I boot up the system and it comes to the desktop with NO icons or menus, sometimes it has a mouse curser..  I am still rather new to the whole Linux thing.. But, I do like it better than W****S..  Please help with this concern!!

all4him

---

### Post by bumanie on 2010-05-12
In terminal try > sudo apt-get install --reinstall ubuntu-desktop

---

### Post by sedawk on 2010-05-12
Can you get access to the text consoles with
either "Alt-F1", "Alt-F2", ... or
"Ctrl-Alt-F1", "Ctrl-Alt-F2".

What I would try to do is to create a new (desktop) user
from command line and check if this problem is related
to the specific (default) user.

Is this a fresh install or an upgrade or ...
What happens if you boot the LiveCD?

---

