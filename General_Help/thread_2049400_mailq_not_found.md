---
title: "mailq not found"
date: 2012-08-28
forum: General Help
---

### Post by xdracco on 2012-08-28
Aloha foums,

I've run into a rather odd issue. When I run mailq from terminal, I get:
```
# mailq
bash: /usr/sbin/mailq: No such file or directory
```mailq does exist but it resides in /usr/bin..
```
# ls -l /usr/bin/mailq
lrwxrwxrwx 1 root root 16 Jul 30 09:41 /usr/bin/mailq -> ../sbin/sendmail
```How in the name of all that is cheesy do I tell my OS that mailq isn't at /usr/sbin but at /usr/bin?

Thanks in advance!

---

### Post by MrGiedi on 2012-08-28
Whats your output of a command? 
> $ echo $PATH
Maybe this directory  usr/bin.mailq isnt in the variable PATH if it isnt than u should add this to the PATH
Tutorial about doing so here [http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm)

---

### Post by xdracco on 2012-08-29
my environment path is fine...

```
# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

For the moment, I've made a symlink. It's a cheap trick. I'm still wondering if there's a database the system user for commands like which, which is able to find binaries on the system...

---

### Post by dcstar on 2012-08-30
> **xdracco said:**
> 
..........
I'm still wondering if there's a database the system user for commands like which, which is able to find binaries on the system...

```
man locate
```

BTW, why are you running a root shell when Ubuntu specifically advises against it?

---

