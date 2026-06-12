---
title: "sometimes can't type new commands in terminal"
date: 2010-05-11
forum: General Help
---

### Post by princeofnam on 2010-05-11
hey, i'm sure most know how to go around this, but when using the terminal to enter everyday commands sometimes it'll hang and not bring me back to the usual user@name:: ~$ prompt again.  I'm not sure how to bring that back up without opening a new window. Retyping it doesn't solve the issue either.

---

### Post by bredman on 2010-05-11
In general, there are three reasons why a command does not terminate

1. The command is doing something useful and will finish when it is ready.
2. The CPU load is high.
3. The process is waiting for something, usually a disk/network.

To eliminate item 1, can you identify if certain commands cause this problem?

To eliminate item 2, run System/Administration/System Monitor and check if the CPU load is rising.

To eliminate item 3, run the command 'top' in another terminal, and check if wa(wait) is greater than id(idle). Press 'q' to exit top.

---

### Post by dcstar on 2010-05-11
> **princeofnam said:**
> hey, i'm sure most know how to go around this, but when using the terminal to enter everyday commands sometimes it'll hang and not bring me back to the usual user@name:: ~$ prompt again.  I'm not sure how to bring that back up without opening a new window. Retyping it doesn't solve the issue either.

Press CTRL-C to terminate the running command.

---

