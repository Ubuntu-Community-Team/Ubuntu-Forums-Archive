---
title: "Behind gui"
date: 2010-04-01
forum: General Help
---

### Post by joshbrice on 2010-04-01
Is there a way to veiw what going on behind the gui in a terminal?

---

### Post by akakingess on 2010-04-01
If you mean something like "Task Manager" within Windows" then you could use either "top" or "htop" both of which you can install with sudo apt get install... and then just run within the terminal by typing top or htop.

---

### Post by joshbrice on 2010-04-01
like this guy wanted "
Is there a way to  have gui picks shown as their  appropriate commands in an xterm as they occur? I'm an old unix user  (and I do mean user - at work the IT department takes care of the  administration. I use the os as a means of getting work done). I'm used  to using an xterm and typing in the commands, and now that I am my own  sys admin, I could do a better job of it if I could 'shadow' what the gui is doing. I know a fair number of commands  to use for other things, but I'm a babe in the woods wrt system  administration."

---

### Post by akakingess on 2010-04-01
Terribly sorry to have misunderstood your question, I will abstain from any further posts.

---

### Post by km0r3 on 2010-04-01
> **joshbrice said:**
> Is there a way to veiw what going on behind the gui in a terminal?

```
strace -p <pid>
```

OR
[URL="http://www.ibm.com/developerworks/library/l-gdb/"]
Getting to know gdb[/URL]

There are probably more ways to go "behind the GUI".

---

