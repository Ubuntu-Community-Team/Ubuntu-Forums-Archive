---
title: "kill a process in a certain amount of time"
date: 2012-05-11
forum: General Help
---

### Post by COKEDUDE on 2012-05-11
I would like to kill a process in a certain amount of time. Can I please get some ideas on how to do this?

---

### Post by Zvlwab on 2012-05-11
The following bash script waits 10 seconds and then kills the process you passed as an argument:
```
#!/bin/bash

sleep 10
kill $1
```

You can add m, h or d to sleep to represent a minute, hour or day.
e.g.
```
sleep 1m
```
will wait for 1 minute.

if you want to pass the name of a process rather than it's PID you should replace kill by killall.

---

### Post by codemaniac on 2012-05-11
or something like that .

```
echo "pkill processname" | at midnight
```

---

### Post by The Cog on 2012-05-11
You could use **at**. This allows you to queue commands for later execution. You enter the at command with a time, like this:
**at 12:21**
and it then gives you an "at> " prompt where you enter all the commands you want to run at that time. Finish the list of commands with Ctrl-D.
Something like this:
```
steve@dingly:~$ killall xeyes
steve@dingly:~$ at 12:21
warning: commands will be executed using /bin/sh
at> killall xeyes
at> <EOT>
job 6 at Fri May 11 12:21:00 2012

```
A one-liner version would be:
```
echo killall xeyes | at 12:25
```

EDIT:
Aargh! codemaniac posted while I was writing (and testing) my answer.

Anyway, here's a nice trick:
```
steve@dingly:~$ at 13:00
at> export DISPLAY=:0.0
at> xeyes -geometry 600x300 &
at> sleep 10
at> killall xeyes
at> <EOT>
```

---

