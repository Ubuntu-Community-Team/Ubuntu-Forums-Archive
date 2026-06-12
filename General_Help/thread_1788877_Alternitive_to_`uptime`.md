---
title: "Alternitive to `uptime`?"
date: 2011-06-23
forum: General Help
---

### Post by jdb91 on 2011-06-23
I'm trying to write a script to gather the uptime of a box and send an email out if the box has died.  Problem being that this is hard when `uptime` changed from the format 23:59 to 1 day.

Is there a method to just see the uptime in hours or minutes or even seconds?

Thanks,
Joe

---

### Post by sisco311 on 2011-06-23
```
cat /proc/uptime
```

The first number is the total number of seconds the system has been up. The second number is how much of that time the machine has spent idle, in seconds.

To get only the uptime, in bash, you can run something like:
```
read -r uptime idle < /proc/uptime
echo "$uptime"
```

---

### Post by ohme on 2011-06-23
using sisco311 idea you could do something like:

echo `cat /proc/uptime | cut -f 1 -d " " `/3600 | bc

to get the uptime in hours

---

### Post by sisco311 on 2011-06-23
> **ohme said:**
> using sisco311 idea you could do something like:

echo `cat /proc/uptime | cut -f 1 -d " " `/3600 | bc

to get the uptime in hours

`COMMANDS` is an older form of the  command substitution. The usage of the POSIX-form $(COMMANDS) is preferred.

In most cases **cat** can be avoided: 

[color=red]cat file | grep PATTERN[/color] #WRONG
[color=green]grep PATTERN file[/color] #CORRECT

[color=red]cat file | tr SET1 SET2[/color] #WRONG
[color=green]tr SET1 SET2 < file[/color] #CORRECT

Since we don't really need to use floating point arithmetics, we don't need to use bc:
```

read -d "." -r uptime < /proc/uptime
((h=uptime/3600))
((m=uptime%3600/60))

echo "uptime: $h hour(s) and $m minute(s)"

```

---

### Post by jdb91 on 2011-06-23
Thanks for all the code, I'm doing it in python rather than shell, so I'm doing it like this:

```
self.uptime = open("/proc/uptime","r").readline().split()[0]
```

Ugly for that bit I know, but it's nicer than piping into BC!


Cheers again!

---

