---
title: "Looking for code to kill a process"
date: 2012-03-12
forum: General Help
---

### Post by Miykel on 2012-03-12
G'Day;  I've been looking for a line of code which shows all running programs in the terminal and allows you to kill one by using the number on the left, I think it starts with  "cp".
Regards Miykel

---

### Post by HermanAB on 2012-03-12
top
htop

---

### Post by wallaroo on 2012-03-12
To list all processes, their 'pid' and their owners ...
```
ps -eaf
```To kill one of your processes ...
```
kill -9 'pid'
```To kill processes not owned by you ...
```
sudo kill -9 'pid'
```

---

### Post by aura7 on 2012-03-12
Another method...
 
ps -e | grep <name of the process>
sudo killall <name of the process>
 
if the first command does not return anything then  you don't have that process running, hence no need to kill it.
 
if it does not works..... then 
 
sudo kill -9 pid 
 
is the best alternate

---

### Post by Miykel on 2012-03-12
Thanks once again guys;  told you it started with cp..........not...........lol.

Many Thanks Miykel

---

