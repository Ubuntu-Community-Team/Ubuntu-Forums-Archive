---
title: "ubuntu server needs to restart every day"
date: 2010-10-21
forum: General Help
---

### Post by arvind_74 on 2010-10-21
Hi Everybody,
I have running web site developed using perl , postgresql data and apache2 web server on ubuntu server needs to restart everyday after it occupies all the 16 GB memory.
if anybody can help me out what's wrong. If we don't restart then system crashes not allow to login.

---

### Post by SeijiSensei on 2010-10-21
Are you asking how you can modify the computer to make it restart automatically, or how to fix the problem with your web site?  The answer to the first is to create the file (with sudo) /var/spool/cron/root then add the entry:

```
01 00 * * * /sbin/shutdown -r now
```

which reboots the computer one minute after midnight each day.

I don't think we can help much with the memory problem, though I'd guess it's something in the perl script.  Neither Apache nor PostgreSQL would eat memory like that in normal use.

---

### Post by arvind_74 on 2010-10-21
Thanks for replying SeijiSensei
I don't know if is there any apache configuration or perl script that making server occupies all the memory and force to restart if it is perl even but there should be settings that apache should not allow use memory more than certain level
is there settings that we can force that perl can't use memory about certain level ?

---

### Post by Grenage on 2010-10-21
I'd personally look at fixing whatever is bleeding the memory!  If it's a perl process, you'll need to debug it.

---

### Post by arvind_74 on 2010-10-21
how to know which one is creating problem is that a perl program or apache ?

---

### Post by Grenage on 2010-10-21
Apache is such a honed, robust system, that it's unlikely to be the cause.  Does *top* give you any clues?

---

### Post by SeijiSensei on 2010-10-21
Just a wild guess, but I'd suspect the perl process creates an array whose size is unbounded.  Whoever wrote the script needs to do some debugging.

A couple of things you might read:
[http://perl.apache.org/docs/1.0/guide/performance.html](http://perl.apache.org/docs/1.0/guide/performance.html)
[http://perl.apache.org/docs/2.0/api/Apache2/Resource.html](http://perl.apache.org/docs/2.0/api/Apache2/Resource.html)
[http://httpd.apache.org/docs/current/mod/core.html#rlimitmem](http://httpd.apache.org/docs/current/mod/core.html#rlimitmem)

---

### Post by sanemanmad on 2010-10-21
Are you running a Database on this site also? what is the disk IO during times you are having this issue?

Have you checked the ulimit settings for the processes? There could be a process opening X files and the mem buffer has hard time. Are you swapping?

---

