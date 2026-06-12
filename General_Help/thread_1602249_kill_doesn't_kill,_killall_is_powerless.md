---
title: "kill doesn't kill, killall is powerless?"
date: 2010-10-21
forum: General Help
---

### Post by Interruptor on 2010-10-21
Today I run OpenOffice.org extensions update and it freezed after showing me that everything was successful.
When i **xkill**ed it it refused to launch without any problem indication.
**killall soffice.bin** didn't report "No process found" after 1,2,3...20 times.
So I tried **killall soffice.bin -i**
```
$ sudo killall soffice.bin -i
Kill soffice.bin(3319) ? (y/N) y
Kill soffice.bin(3319) ? (y/N) y
Kill soffice.bin(3319) ? (y/N) y
Kill soffice.bin(3319) ? (y/N) y
Kill soffice.bin(3319) ? (y/N) y
Kill soffice.bin(3319) ? (y/N) y
...
```

The only command that killed it was **kill -KILL 3319**.
Did someone changed default kill signal? Police? :D

---

### Post by terdon on 2010-10-21
Try ```
killall -9 soffice.bin
```

Generally with this kind of thing it is better to use kill and the process id. So, to get the process id:```
 ps a | grep soffice
```
You should get something like:```
ps a| grep soffice
10798 pts/5    Sl     0:00 /usr/lib/openoffice/program/soffice.bin -splash-pipe=5
10825 pts/6    S+     0:00 grep --color soffice

```
The number in the first column is the process id (PID), 10798 in this example, once you have that do:```
kill 10798
``` and if that doesn't work, force kill:```
kill -9 10798
```

---

