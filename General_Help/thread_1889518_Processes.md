---
title: "Processes"
date: 2011-12-01
forum: General Help
---

### Post by smss on 2011-12-01
Hello.
how to see the all processes in the terminal?
and how to kill one processes (in terminal)?
and at end ; how to clean the memory(in terminal)?(RAM)
Thanks.

---

### Post by WorMzy on 2011-12-01
> how to see the all processes in the terminal?

```
ps aux
```

> and how to kill one processes (in terminal)?

```
kill [COLOR="Red"]processid[/COLOR]
```
or
```
pkill [COLOR="Red"]processname[/COLOR]
```
or
```
killall [COLOR="Red"]processname[/COLOR]
```

> and at end ; how to clean the memory(in terminal)?(RAM)

You don't. Leave that to the system.

---

### Post by smss on 2011-12-01
I can not clean the memory??
I see a person in the OpenSuse for this mean using a command as "distclean" and can,But i do not trustful of this command.

---

### Post by ajgreeny on 2011-12-01
Why do you want to purge your memory of its data content?  It will all be cleared when you shutdown.

If you are concerned about the apparent high ram usage of Ubuntu in particular, or Linux in general, remember that Linux manages ram quite differently from Windows, working on the principle that unused ram is wasted.  It therefore keeps data in ram, once it has been put there until such time as more free ram is required.

If you use the command ```
free -m
``` it will show an output like 
```
             total       used       free     shared    buffers     cached
Mem:          2012       1960         52          0         93       1292
-/+ buffers/cache:        574       1438
Swap:         2047          0       2047
```where the ram presently used on my system is 1960MB out of 2012MB therefore only 52MB is empty.  The important figure, however, is the -/+buffers/cache which shows that 574MB is being used by active processes and 1438MB are available, though not empty.

This is all done this way to make your system faster and more efficient.

---

### Post by WorMzy on 2011-12-01
> **smss said:**
> I can not clean the memory??
I see a person in the OpenSuse for this mean using a command as "distclean" and can,But i do not trustful of this command.

"distclean" is often a make target which cleans up a compile directory. It doesn't clean RAM, and you probably won't ever need to use it while on Ubuntu.

---

