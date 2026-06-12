---
title: "Crontab Env not working with Script"
date: 2011-10-04
forum: General Help
---

### Post by miimnon on 2011-10-04
I cannot get gnome-terminal to launch from a crontab. How do I accomplish this task?

I have tried this so far.

```
* * * * * . /home/buddy/.bashrc ; /home/buddy/script.sh
```


```
* * * * * . /home/buddy/.profile ; /home/buddy/script.sh
```


```
* * * * * . /home/buddy/.bashrc ; /usr/bin/gnome-terminal
```



Nothing works. Help.

---

### Post by dcstar on 2011-10-05
> **miimnon said:**
> I cannot get gnome-terminal to launch from a crontab. How do I accomplish this task?
......

Any graphical application needs the specific output screen set, do a web search on this.

---

