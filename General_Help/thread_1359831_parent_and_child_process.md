---
title: "parent and child process"
date: 2009-12-20
forum: General Help
---

### Post by georgestan on 2009-12-20
Hello,

I want to ask a question on the parent-child process handling.

Suppose a child process is created from its parent, say, launch a firefox from gnome-terminal.

When the parent process is closed, sometimes the child process is closed as well, other times the child process stays intact. Anyone has knowledge on the mechanism of determining whether to close or not?

I know that in Windows, when a parent is closed, all its children become children of explorer.exe so that they won't be closed.

Regards

---

### Post by SecretCode on 2009-12-20
I don't know about the internal mechanisms affecting it, but for commands issued from a shell you can use the nohup command to prevent the child process from closing when you close the shell.

[nohup(1) - Linux man page](http://linux.die.net/man/1/nohup)

---

### Post by nikhilbhardwaj on 2009-12-20
technically i think the children processes should close when the parent process closes

yes nohup allows the processes to run even after you logout

---

