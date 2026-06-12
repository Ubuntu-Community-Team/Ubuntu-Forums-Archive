---
title: "grep help in ps"
date: 2011-06-02
forum: General Help
---

### Post by COKEDUDE on 2011-06-02
How would I do something like this with numbers **ps -ef | grep [f]irefox**? This ignores the **grep --colour=auto firefox** garbage. When I do **~ $ ps -ef | grep [3]470** it doesn't ignore the **grep --colour=auto [3]470** garbage.


```
~ $ ps -ef | grep [3]470
bob       3470  3467  0 18:14 pts/0    00:00:00 bash
bob       3714  3470  0 18:40 pts/0    00:00:00 ps -ef
bob       3715  3470  0 18:40 pts/0    00:00:00 grep --colour=auto [3]470
~ $ ps -ef | grep firefox
bob       2102     1  4 15:36 ?        00:08:43 /usr/lib/firefox-3.6.17/firefox-bin
bob       2165  2102  3 15:37 ?        00:05:30 /usr/lib/firefox-3.6.17/plugin-container /usr/lib/adobe-flashplugin/libflashplayer.so 2102 plugin true
bob       3717  3470  0 18:40 pts/0    00:00:00 grep --colour=auto firefox
~ $ ps -ef | grep [f]irefox
bob       2102     1  4 15:36 ?        00:08:43 /usr/lib/firefox-3.6.17/firefox-bin
bob       2165  2102  3 15:37 ?        00:05:30 /usr/lib/firefox-3.6.17/plugin-container /usr/lib/adobe-flashplugin/libflashplayer.so 2102 plugin true
```

---

### Post by TeoBigusGeekus on 2011-06-02
It works here (Arch Linux)
```
[[Time:02:05 Location:~/Desktop]]
$ ps aux | grep 4762
teo       4762  0.2  1.8  92284 19092 pts/0    Ss+  00:28   0:15 rtorrent
teo       6515  0.0  0.0   4408   828 pts/1    S+   02:05   0:00 grep 4762
[[Time:02:05 Location:~/Desktop]]
$ ps aux | grep [4]762
teo       4762  0.2  1.7  92288 17808 pts/0    Ss+  00:28   0:15 rtorrent
```
Maybe it's a dash thing?

---

### Post by COKEDUDE on 2011-06-02
> **TeoBigusGeekus said:**
> It works here (Arch Linux)
```
[[Time:02:05 Location:~/Desktop]]
$ ps aux | grep 4762
teo       4762  0.2  1.8  92284 19092 pts/0    Ss+  00:28   0:15 rtorrent
teo       6515  0.0  0.0   4408   828 pts/1    S+   02:05   0:00 grep 4762
[[Time:02:05 Location:~/Desktop]]
$ ps aux | grep [4]762
teo       4762  0.2  1.7  92288 17808 pts/0    Ss+  00:28   0:15 rtorrent
```
Maybe it's a dash thing?

Two problems. You don't have an alias in grep like me. The parameters in aux and -ef in ps are different. 

```

~ $ ps aux | grep 3470
bob       3470  0.0  0.0   7472  2236 pts/0    Ss   18:14   0:00 bash
bob       5482  0.0  0.0   3492   988 pts/0    S+   21:12   0:00 grep --colour=auto 3470
~ $ ps aux | grep [3]470
bob       3470  0.0  0.0   7472  2236 pts/0    Ss   18:14   0:00 bash
~ $ alias grep
alias grep='grep --colour=auto'

```

---

### Post by ruffEdgz on 2011-06-02
@COKEDUDE
I'm curious now why your grep is doing that because doing similar grep commands with ps, I don't get it:
```

ps -ef | grep [6]769
root      6769   407  0 22:25 ?        00:00:00 udevd --daemon

ps -ef | grep udevd
root       407     1  0 11:37 ?        00:00:00 udevd --daemon
root      6768   407  0 22:25 ?        00:00:00 udevd --daemon
root      6769   407  0 22:25 ?        00:00:00 udevd --daemon
bdflemin  6915  3844  0 23:00 pts/1    00:00:00 grep --color=auto udevd

ps -ef | grep [u]devd
root       407     1  0 11:37 ?        00:00:00 udevd --daemon
root      6768   407  0 22:25 ?        00:00:00 udevd --daemon
root      6769   407  0 22:25 ?        00:00:00 udevd --daemon

```
I do have Ubuntu 10.10 desktop right now and I can't seem to get the same thing as you are using [] in the grep statement.

---

### Post by Vaphell on 2011-06-03
by coincidence the number is listed not in command name but in parrent process id, so there will be a match
> ```
~ $ ps -ef | grep [3]470
bob       3470  3467  0 18:14 pts/0    00:00:00 bash
bob       3714  3470  0 18:40 pts/0    00:00:00 ps -ef
bob       3715  [COLOR="Blue"]3470[/COLOR]  0 18:40 pts/0    00:00:00 grep --colour=auto [3]470
```

either way
```
ps -ef | grep <whatever> | grep -v grep
``` will filter the grep line out

---

### Post by DaithiF on 2011-06-03
or just use pgrep

---

### Post by Habitual on 2011-06-04
> **DaithiF said:**
> or just use pgrep

thank you!

---

