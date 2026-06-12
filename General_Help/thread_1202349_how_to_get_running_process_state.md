---
title: "how to get running process state"
date: 2009-07-02
forum: General Help
---

### Post by dileep.kk on 2009-07-02
Hi,I am writing network module (LKM). I got process information by current->pid and current->comm. But now i want current state of task. I want to know the state of running the process. I dont find any information in struct task_struct structure. how can i get the state of current running process.

---

### Post by WRDN on 2009-07-02
To get the state (and other information), use:

```
ps aux
```

To just list the states (why you would want to, I'm not sure):

```
ps aux | awk '{print $8}'
```

Or for a specific process:

```
ps aux | grep [PROCESS_NAME or `pidof PROCESS_NAME`] | awk '{print $8}'
```

In the above 2 cases, awk is used to print a specific section of the result. $8 refers to the 8th column, and grep is used to find what you are looking for.

As another example, here is a section from the output of ps aux on my system:

> 
username   7227  0.0  0.1 157128  7944 pts/1    Sl+  11:43   0:00 vim cv
username   7235  0.0  0.1  21816  4632 pts/2    Ss+  11:44   0:00 bash
username   7278  0.0  0.0  19116  1360 pts/2    T    11:45   0:00 top


For many processes, "pts/X" will be replaced with "?" (X refers to a number e.g. pts/1 or pts/2 as seen above).

As can be seen, the process status is in the 8th column. If for example, you wanted to print the process ID only, you would replace $8 with $2.

---

