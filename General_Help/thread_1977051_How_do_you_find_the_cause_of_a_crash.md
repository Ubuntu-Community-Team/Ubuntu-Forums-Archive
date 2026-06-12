---
title: "How do you find the cause of a crash?"
date: 2012-05-09
forum: General Help
---

### Post by xjonquilx on 2012-05-09
I tried asking this on AskUbuntu but it just got voted down. I've tried searching Google and I cannot find the answer to this question. I don't see what is so wrong with my question?

Anyways, my question is this: How can you find out what program is crashing and causing the error reporting tool to come up? It keeps happening and I don't see an option anywhere to view the report.

---

### Post by cortman on 2012-05-09
One good way to find the cause of a program crashing is to launch it from a terminal. If rhythmbox keeps crashing on me, I'd open a terminal and type

```
rhythmbox
```

All errors will be printed in the terminal.
If you're talking about a system crash, there are many logs to view. dmesg is one of the primary ones, simply type it in a terminal.

---

### Post by bogan on 2012-05-10
Hi!, **xjonquilx**.

If this is with the 12.04 error reporting faculty: Click on the 'Details' button and **wait**.

It will show the path and a rotating cursor, eventually the error report will display and that tells you which program is at fault or crashed.

You may have to click on some authorizations to get there.

Chao!, **bogan**.

---

