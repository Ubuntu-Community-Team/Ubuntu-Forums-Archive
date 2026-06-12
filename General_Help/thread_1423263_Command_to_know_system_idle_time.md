---
title: "Command to know system idle time"
date: 2010-03-06
forum: General Help
---

### Post by shashanksingh on 2010-03-06
I need a command which can tell me how long the system has been idle or rather how long the CPU usage is negligible which can be run by any user...

---

### Post by flippo on 2010-03-06
top?

---

### Post by shashanksingh on 2010-03-07
I want to figure a way to know the idle time of the system...
The problem is that it hardly is idle, I mean top is too precise. It shows all the services and some minute percentage of cpu is always used.
And besides I want to extract the data from top into a program and the execution of the program depends on the system idle time.
Any ways I can do that?

---

### Post by pbrane on 2010-03-07
You can try this:
```

top -n 1 | grep "Cpu(s):" | awk '{print $5}'

```
if you run top "out of the box"

or this if you have more than one core and use the command to display all cores
```

top -n 1 | grep "Cpu0" | awk '{print $6}'

```
This only shows cpu idle time for core 0 though.

---

### Post by shashanksingh on 2010-03-09
Nice..
Thanks

---

### Post by asmoore82 on 2010-03-09
are you looking to queue "batch" jobs?
[Quote=man batch]**batch** executes commands when system  load  levels  permit;  in  other words, when
the  load  average  drops below 1.5, or the value specified in the invocation of atd.[/QUOTE]

see ```
man batch
```

---

