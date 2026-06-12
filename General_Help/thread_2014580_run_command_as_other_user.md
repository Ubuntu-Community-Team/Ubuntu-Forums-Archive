---
title: "run command as other user"
date: 2012-07-02
forum: General Help
---

### Post by Drenriza on 2012-07-02
Hey guys.

I would like to run a series of command from the root user as another user with the 

```
su USERNAME -c COMMAND
``` command.

But i'am realising that their is a problem when having a space in the command. For example

```
su user -c ls -l
```

How can you do so you can run a longer command where you pipe the result to other commands and so on, without the su command breaking?

Kind regards.

---

### Post by dino99 on 2012-07-02
try with alias redefined (created) under .bashrc

---

### Post by Lars Noodén on 2012-07-02
Also try with quotes around it.

```

su user -c "ls -l"

```

---

