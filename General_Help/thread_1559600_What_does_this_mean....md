---
title: "What does this mean...???"
date: 2010-08-23
forum: General Help
---

### Post by robertcoulson on 2010-08-23
Was playing around in the terminal and typed in "uptime"...I noticed as per the attachment that it said " 2 users"...Is that normal...???
Robert

---

### Post by Bachstelze on 2010-08-23
Yes, one for your X session and one for your terminal session.  You can use the [font=monospace]who[/font] command to see a detail of opened sessions.

---

### Post by robertcoulson on 2010-08-23
Bachstelze....Sooooo, that IS normal....?
Robert

---

### Post by robertcoulson on 2010-08-23
Bachstelze...Tried your "who" in the terminal and got this (see attachment).
Robert

---

### Post by Bachstelze on 2010-08-23
> **robertcoulson said:**
> Bachstelze...Tried your "who" in the terminal and got this (see attachment).
Robert

That's what I said: tty7 is your X (graphical) session, and pts/0 is your terminal session (if you run the command [font=monospace]tty[/font] in your terminal, it will output [font=monospace]/dev/pts/0[/font]).

---

### Post by robertcoulson on 2010-08-23
Thanks Bachstelze, I am a little stupid I guess...Thanks for your help.
Robert

---

