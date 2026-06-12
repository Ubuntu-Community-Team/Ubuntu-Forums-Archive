---
title: "Multiple commands in one shortcut"
date: 2010-02-06
forum: General Help
---

### Post by Eragon0605 on 2010-02-06
I am wondering how I can get a shortcut to open a terminal, cd to a directory, and execute a command. I am running Ubuntu 9.10.

---

### Post by kaibob on 2010-02-06
> **Eragon0605 said:**
> I am wondering how I can get a shortcut to open a terminal, cd to a directory, and execute a command. I am running Ubuntu 9.10.

The answer depends a bit on the command and what you want to happen after the command is executed, but the following is an example that leaves the terminal window open:

```
gnome-terminal --execute bash -c "cd /home/kaibob ; echo 'hello world' ; bash"
```

---

### Post by sgosnell on 2010-02-06
A bash script can do almost anything you like, in any order.

---

### Post by Eragon0605 on 2010-02-07
Thanks! Exactly what I was looking for.

---

