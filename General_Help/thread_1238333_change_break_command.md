---
title: "change break command?"
date: 2009-08-12
forum: General Help
---

### Post by evencoil on 2009-08-12
The default command to end a program's execution in the terminal is <Ctrl + C>. However I remapped Copy in the GNOME Terminal from its default <Ctrl> + <Shift> + C to <Ctrl> + C and now the program break command won't issue. I'd like to change the program break to be <Ctrl + Pause>. Does anyone know how to do this? Is there a line I put in my bash config that will achieve this? Thanks!

---

### Post by ibuclaw on 2009-08-12
Don't think that is possible...

You could use the SIGQUIT as an alternative. That is **Ctrl+4**

Regards
Iain

---

### Post by evencoil on 2009-08-12
that seems to work alright, thanks!

what's the difference between SIGQUIT and <Ctrl> + C?

---

### Post by ibuclaw on 2009-08-12
> **evencoil said:**
> that seems to work alright, thanks!

what's the difference between SIGQUIT and <Ctrl> + C?

Ctrl+4 - SIGQUIT - Send signal to quit the application.
Ctrl+C - SIGINT - Send signal to interrupt the application.

There is a slight difference between the two. I think it was that SIGINT is more forceful.

Regards
Iain

---

### Post by evencoil on 2009-08-12
got it, thanks again!

---

