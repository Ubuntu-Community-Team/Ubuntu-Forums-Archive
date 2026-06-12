---
title: "Auto run a program after a login on a specific console"
date: 2011-12-28
forum: General Help
---

### Post by Cool Javelin on 2011-12-28
I would like to automatically run a program when I log on to a specific console (tty1) and no other.

I am running Ubuntu server 10.10 (no x) and I added the following line to my /etc/init/tty1.conf to automatically log me in to the first console and it works.

exec /bin/login -f USERNAME < /dev/tty1 > /dev/tty1 2>&1

I have a program (called HomeAuto) that monitors a special data acquisition board and I want it to start when this console logs in.

Is it a matter of simply adding another line to that file too?

Thanks, Mark.

---

### Post by Cool Javelin on 2012-01-04
I found my answer.

I put a line at the bottom of my ~/.bashrc file. The line reads:

```
[[ $(tty) == '/dev/tty2' ]] && /path/to/command/name_of_command
```

This runs the command when I log into tty2

Mark.

---

### Post by sisco311 on 2012-01-05
I'd put it in ~/.bash_profile which is executed only for login shells. While ~/.bashrc is executed each time you start an interactive shell.

More info here:   [http://mywiki.wooledge.org/DotFiles](http://mywiki.wooledge.org/DotFiles)

---

