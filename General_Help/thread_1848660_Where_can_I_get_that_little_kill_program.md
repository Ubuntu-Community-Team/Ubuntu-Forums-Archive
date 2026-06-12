---
title: "Where can I get that little kill program"
date: 2011-09-22
forum: General Help
---

### Post by jacatone on 2011-09-22
I'm running Ubuntu 10.04 LTS and remember there was a little "X" program or utility that that would close hanged programs in Linux. Anyone know what it was? Thanks.

---

### Post by bodhi.zazen on 2011-09-22
xkill ?

You can also terminate programs from the command line with kill, killall, etc - see the man pages for details.

```
kill -9 PID
killall foo
```

---

### Post by jacatone on 2011-09-23
Don't find anything under xkill. This was a little program that when opened showed you an X. You'd place it over the hanged program and click it and the program would close. Can't remember the name of it.

---

### Post by patryk77 on 2011-09-23
Force Quit Applet?

If you are using gnome, right-click on a panel and choose "Add to Panel" Then just select "Force Quit".

It shows me a +, not an x, but it might be an x after I finish this port :P

---

### Post by bodhi.zazen on 2011-09-23
> **jacatone said:**
> Don't find anything under xkill. This was a little program that when opened showed you an X. You'd place it over the hanged program and click it and the program would close. Can't remember the name of it.

apt-get install xkill

[http://manpages.ubuntu.com/manpages/natty/man1/xkill.1.html](http://manpages.ubuntu.com/manpages/natty/man1/xkill.1.html)

---

