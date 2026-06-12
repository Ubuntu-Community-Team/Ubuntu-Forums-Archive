---
title: "Display= : ?"
date: 2009-10-04
forum: General Help
---

### Post by rob86 on 2009-10-04
I'm interested in what this "DISPLAY=" thing does. Could someone tell me a bit about it? Does it have something  to those different terminals that pop up when you do CTRL+ALT F1,F2... ?

---

### Post by falconindy on 2009-10-04
the DISPLAY variable is the active output assigned to a session. It can be graphical (gnome, kde, etc) or for a terminal session (ttyX). If you open a terminal, and type `who`, you'll get an example of possible values for DISPLAY.

---

### Post by Diabolis on 2009-10-04
The terminals are **TTY**s, virtual terminals. **$DISPLAY** is a **environment variable**.

You can see which display you are using with this command:
```
echo $DISPLAY
```

---

### Post by rob86 on 2009-10-04
What you both said makes sense thanks. I opened up and logged into a virtual terminal (tty1) and when I type the who command (on tty7), it is listed but there is no :1 or anything else beside it. 

So just for an example, how would I send the output from a Gnome-Terminal on tty7, to tty1? I tried something like, $DISPLAY='tty1' but that didn't work and had an error.

---

### Post by Diabolis on 2009-10-04
They totally 2 different things.

Virtual terminals allow you to have multiple users log in at the same machine. The environment variable $DISPLAY tells that machine to which DISPLAY, a screen/monitor usually, send its output.

---

