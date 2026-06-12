---
title: "Ubuntu 10.10 windows button problems"
date: 2010-10-26
forum: General Help
---

### Post by neroubas on 2010-10-26
i have a problem that i cannot understand how it happened.the 3 buttos for close minimize and maximize for some reason have gone right and at left i have a small white dot when it's pressed it shows whatever right click at the windows bar shows.what happened?how to fix it?

---

### Post by ch1ll1man on 2010-10-26
You can use gconf from the command line to switch them

For left use this

**gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:**"

For right use this

**gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:minimize,maximize,close"**

Run the above commands from the terminal.

You may have switched themes.

---

### Post by neroubas on 2010-10-26
thank you very much but i don't remember changing anything and this is why i was so concerned

---

### Post by ch1ll1man on 2010-10-26
It's 10.10 and you could have come across a bug.  I hope you've managed to switch it back using the gconf commands I gave.

---

### Post by Grenage on 2010-10-26
Edit: Retarded moment.

---

