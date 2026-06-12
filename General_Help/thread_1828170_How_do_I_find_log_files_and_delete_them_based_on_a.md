---
title: "How do I find log files and delete them based on age"
date: 2011-08-18
forum: General Help
---

### Post by mashedbear on 2011-08-18
Hi I want find a bunch of log files and delete ones that are older than say 5 days. Ideally I would then like to add this my crontab to run once a day. 

The log files are in /var/log and are owned by root.

They have a standard naming convention which is [date]RootCronRsync-backupHOME.log  

An example file is 20100621RootCronRsync-backupHOME.log

Trying to put together a bash script to do this I think I need something like 

```
find /var/log/ -name *RootCronRsync-backupHOME.log -mtime +5 -exec rm {} \;
``` 

However if I try this without the -exec rm (ie to see if I can find the right files first) I get the following error

> find: paths must precede expression: 20090405RootCronRsync-backupHOME.log
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

There is no doubt a better way to do this. Thanks for any help / advice.

---

### Post by tredegar on 2011-08-18
Maybe try 
```
find /var/log/ -name [COLOR="Red"]\[/COLOR]*RootCronRsync-backupHOME.log -mtime +5 -exec rm {} \;
```
* is interpreted by bash before the arguments are passed to the **find** command. This can make it messy, so try escaping it from the shell.

See **man bash** (it's a *big* file ;) )

---

### Post by TeoBigusGeekus on 2011-08-18
No problem here; could it be a dash thing?
Try adding
```
#!/bin/bash
```
at the top.

---

### Post by TeoBigusGeekus on 2011-08-18
> **tredegar said:**
> Maybe try 
```
find /var/log/ -name [COLOR="Red"]\[/COLOR]*RootCronRsync-backupHOME.log -mtime +5 -exec rm {} \;
```
* is interpreted by bash before the arguments are passed to the **find** command. This can make it messy, so try escaping it from the shell.

See **man bash** (it's a *big* file ;) )

Can't be man...
The -name switch in find is supposed to accept wildcard characters as is.

---

### Post by tredegar on 2011-08-18
> Can't be man...
The -name switch in find is supposed to accept wildcard characters as is. 
Can be:```
tred@laptop:~$ find . -name *  -mtime +5 -exec [COLOR="Red"]ls -l[/COLOR]  {} \;
find: paths must precede expression: 2010-11-19.pdf
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
tred@laptop:~$ find . -name [COLOR="Red"]\[/COLOR]*  -mtime +5 -exec [COLOR="Red"]ls -l[/COLOR]  {} \;
*A _long_ list follows ....*

```

**bash** is neat, smart and wicked, so it can turn right round and BITE you in the a?? ;)

---

### Post by TeoBigusGeekus on 2011-08-18
You're right! Another way to do it is this
```
find . -name "*" -mtime +5 -exec ls -l  {} \;
```

---

### Post by sisco311 on 2011-08-18
I would use a single log file and logrotate to 'rotate' it and remove the old ones.

---

### Post by TeoBigusGeekus on 2011-08-18
> **sisco311 said:**
> I would use a single log file and logrotate to 'rotate' it and remove the old ones.

+1
Nice idea.

---

### Post by mashedbear on 2011-08-19
Thanks all. 

```
find /var/log/ -name [COLOR="Red"]\[/COLOR]*RootCronRsync-backupHOME.log
```

solves the problem :D 

Would like to understand about logrotate - that sounds better. Will look into this.

---

