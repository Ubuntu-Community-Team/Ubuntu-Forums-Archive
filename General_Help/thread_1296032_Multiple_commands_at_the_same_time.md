---
title: "Multiple commands at the same time"
date: 2009-10-20
forum: General Help
---

### Post by Intrepid Ibex on 2009-10-20
Hi,

How can I execute e.g. firefox and gedit at the same time, as this only launches gedit _after_ ff has closed/quit:
```
firefox; gedit
```

- Thanks

---

### Post by sisco311 on 2009-10-20
```
firefox & gedit
```

If a command is terminated by the control operator &,  the  shell  executes  the command in the background in a subshell.  The shell does not wait for the command to finish, and the return status is  0.   Commands separated  by  a  ; are executed sequentially; the shell waits for each command to terminate in turn.

---

### Post by Intrepid Ibex on 2009-10-20
Sweet, thanks.

---

