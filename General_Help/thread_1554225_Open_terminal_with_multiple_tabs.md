---
title: "Open terminal with multiple tabs?"
date: 2010-08-16
forum: General Help
---

### Post by BUSHYBOB on 2010-08-16
Is it possible to open a terminal window with a few tabs and execute a separate script or command in each with a single command or script?

---

### Post by DaithiF on 2010-08-16
Not in gnome-terminal if I remember correctly.

I would use screen for something like this.  You could open a screen session with multiple windows and a command executing in each.

---

### Post by jv2112 on 2010-08-16
Try Terminator:D

---

### Post by Vaphell on 2010-08-16
[http://stackoverflow.com/questions/1188959/open-a-new-tab-in-gnome-terminal-using-command-line](http://stackoverflow.com/questions/1188959/open-a-new-tab-in-gnome-terminal-using-command-line)

---

### Post by BUSHYBOB on 2010-08-16
> **Vaphell said:**
> [http://stackoverflow.com/questions/1188959/open-a-new-tab-in-gnome-terminal-using-command-line](http://stackoverflow.com/questions/1188959/open-a-new-tab-in-gnome-terminal-using-command-line)

Cheers, that works.

Here's what I am doing

```
gnome-terminal --tab -e 'ssh myserver' --tab -e 'ssh myserver'
```Which opens a terminal with two tabs both logged onto myserver.

I want to run commands on on the remote machine but I'll start a new thread for that and mark this one solved.

---

