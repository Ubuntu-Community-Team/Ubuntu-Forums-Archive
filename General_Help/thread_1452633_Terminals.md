---
title: "Terminals"
date: 2010-04-12
forum: General Help
---

### Post by ReeRD on 2010-04-12
Is CTRL+ALT+F7 the default GUI terminal used by Ubuntu 9.10? Or is it CTRL+ALT+F9? Is there a way to check via some shell command which terminal I'm currently logged into?

---

### Post by geirha on 2010-04-12
When X starts, it grabs the first available tty, which is usually tty7.
tty1-6 are set to virtual consoles during boot, and to tty8 some boot messages gets sent, so that's "taken" as well.

You can use the commands *w* and *who* to get a list of currently logged in users, including which tty they're logged in at.

---

### Post by change_mode on 2010-04-12
> **ReeRD said:**
> Is there a way to check via some shell command which terminal I'm currently logged into?

Try the 'w' or 'who' commands.

edit: Seems like I'm a bit late ;)

---

### Post by ReeRD on 2010-04-12
Thanks.

Btw, I found that "sudo fgconsole" tells you the terminal number as well.

---

