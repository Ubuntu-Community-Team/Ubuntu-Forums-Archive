---
title: "What to do in case of not responsive desktop?"
date: 2012-07-10
forum: General Help
---

### Post by timetopat on 2012-07-10
Lets say I downloaded something like Alien Arena and I have had a problem where it stopped responding(This happens with other programs) or goes black, what should I do?  My friends recommend using the terminal to find and kill the task.  I notice that some games or other applications sometimes do this and I am unsure what to do in that scenario.  Is the terminal the only way to regain control or can something else be done?  What do you do in these cases?

---

### Post by cortman on 2012-07-10
> **timetopat said:**
> Lets say I downloaded something like Alien Arena and I have had a problem where it stopped responding(This happens with other programs) or goes black, what should I do?  My friends recommend using the terminal to find and kill the task.  I notice that some games or other applications sometimes do this and I am unsure what to do in that scenario.  Is the terminal the only way to regain control or can something else be done?  What do you do in these cases?

If only one program has locked up and you still can manipulate the desktop, you can kill the process most easily with a terminal.
List running processes with

```
ps -ef
```

Which will be a lot of processes. Narrow it down with grep-

```
ps -ef | grep alien
```

will list only running process with the word "alien" in the process name. Kill processes with

```
kill -9 process_id
```

The process ID is the 4+ digit number in the second column in ps. If the process was started by root (i.e., installing software, making system changes) you'll need to use sudo with kill -9.

Just a rough overview.

---

