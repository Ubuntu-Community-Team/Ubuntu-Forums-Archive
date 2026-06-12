---
title: "Expect script with 'at'"
date: 2009-10-19
forum: General Help
---

### Post by renkinjutsu on 2009-10-19
```
#!/usr/bin/expect

spawn deluge-console
send "resume *\n"
send "exit\n"
expect eof

```

been using that for a while.. The command works when executed in the terminal, but it doesn't work with 'at'
```
echo command | at <time>
```

and when i had a look at `top`, i saw that everytime i ran the command with 'at', there appeared `deluge-console <defunct>` Why is it defunct? and the script opens, why doesn't it execute properly? Need some help.

---

### Post by alphaniner on 2009-10-19
I know that **cron** can't launch GUI apps without some extra information, maybe **at** is similar.

---

### Post by Giblet5 on 2009-10-19
Zombie attack. 

The defunct procs are because that command finished and expect is still running, but has not called wait(2) to clean up after itself.

Why might expect freeze up? Maybe expect wants to flush the input stream...who knows.

I would wrap your script for the shell ```
#!/bin/sh

/usr/bin/expect << ! > /dev/null 2>&1
spawn deluge-console
send "resume *\n"
send "exit\n"
expect eof
!

exit 0
``` and run that wrapper from at.

You could do accomplish the same thing from cron with your existing script, but you use at...

---

### Post by renkinjutsu on 2009-10-19
it's not a gui app though.. it uses deluge's console interface and also runs perfectly in the terminal, pause/resumes all torrents

---

### Post by renkinjutsu on 2009-10-19
> **Giblet5 said:**
> Zombie attack. 

The defunct procs are because that command finished and expect is still running, but has not called wait(2) to clean up after itself.

Why might expect freeze up? Maybe expect wants to flush the input stream...who knows.

I would wrap your script for the shell ```
#!/bin/sh

/usr/bin/expect << ! > /dev/null 2>&1
spawn deluge-console
send "resume *\n"
send "exit\n"
expect eof
!

exit 0
``` and run that wrapper from at.

You could do accomplish the same thing from cron with your existing script, but you use at...

thanks for the wrapper, but even with it, at still isn't doing its thing.. But it redirected the output to null, so that was a breath of fresh air

---

### Post by Giblet5 on 2009-10-19
> **renkinjutsu said:**
> it's not a gui app though.. it uses deluge's console interface and also runs perfectly in the terminal, pause/resumes all torrents

Many programs will attempt to flush the stdin (aka keyboard)at some point. Those programs assume that stdin is file descriptor 0. If you provided a file descriptor 0, like from a shell, that will work.

If not, it may do unpredictable things, but hanging is the most common by far.

Try the example I provided or use cron with all three stdio file descriptors explicitly redirected.

---

### Post by Giblet5 on 2009-10-19
> **renkinjutsu said:**
> thanks for the wrapper, but even with it, at still isn't doing its thing.. But it redirected the output to null, so that was a breath of fresh air

If that really IS your complete script, why not just do it straight from the shell?

```
#!/bin/sh

deluge-console << ! > /dev/null 2>&1
resume *
exit
!

exit 0
``` and run THAT from at.

That's debuggable too. ;)

---

### Post by benj1 on 2009-10-19
failing that it could be that (i think) at uses cron, cron runs as root and so its starting deluge as root.
if thats the case you might want to set up cron to run as the user and run at through a user cron job.

---

### Post by renkinjutsu on 2009-10-19
i had no idea that was possible, but the redirection to /dev/null made it not work for some reason... begone, expect!

doesn't work with at, still

---

### Post by renkinjutsu on 2009-10-19
> **benj1 said:**
> failing that it could be that (i think) at uses cron, cron runs as root and so its starting deluge as root.
if thats the case you might want to set up cron to run as the user and run at through a user cron job.

both cron and at run as the user that created the job, no?

---

### Post by Giblet5 on 2009-10-19
> **renkinjutsu said:**
> both cron and at run as the user that created the job, no?

Yes. Both cron and at run as the user, but without the full user environment. Make no assumptions about current working directory, PATH variable, TERM variable, etc, or you'll have a grand time debugging your script.

A handy way to establish some sanity for cron/at scripts is to add some muck to the top of your scripts ```
#!/bin/bash

. /etc/login.defs
cd /home/MyUserName

...
```

You can enable debugging by inserting ```
set -xv
```

---

### Post by Giblet5 on 2009-10-19
> **renkinjutsu said:**
> i had no idea that was possible, but the redirection to /dev/null made it not work for some reason... begone, expect!

doesn't work with at, still


Make sure that your script, which will run from at, provides the exact and specific environment that you need at runtime:

Explicitly go to the correct directory. Don't assume.

Specify commands with the full path name - it's much faster.

Make sure your command usage is correct.

If there's still trouble, use the 'set -xv' trick and redirect to a logfile. Maybe there's something obvious there.

---

### Post by renkinjutsu on 2009-10-19
even with complete path names, it doesn't work!

and if i redirect ! to a log file, and run it from terminal, there's content, but if i run it from at, the log file is created, but there is NO content.. and i know deluge-console is being executed because i get the defunct process, but it's the pause and exit that aren't getting through

---

### Post by Giblet5 on 2009-10-19
> **renkinjutsu said:**
> even with complete path names, it doesn't work!

and if i redirect ! to a log file, and run it from terminal, there's content, but if i run it from at, the log file is created, but there is NO content.. and i know deluge-console is being executed because i get the defunct process, but it's the pause and exit that aren't getting through

Interesting.

This is definitely a problem with deluge-console. It seems to rely on the terminal.

How comfy are you with python programming?

---

### Post by renkinjutsu on 2009-10-19
Don't know anything about python..

---

### Post by stylishpants on 2009-10-19
I don't know anything about the executable named 'deluge-console'.  However, in my own deluge wrapper script I make heavy use of this form of command for scripting the deluge console:
```
 deluge -u console -a "<command>" 
```

This form does not require any kind of input redirection to feed in commands.  

The ubuntu package "deluge-console" must be installed to use this.

Try something like this:
```

echo 'deluge -u console -a "resume all"' | at now + 1 minute

```

---

### Post by renkinjutsu on 2009-10-19
the executable deluge-console comes from me compiling deluge 1.2.0rc1 (but `deluge -u console` still works) and `deluge` does have an -a option but when i try to pass a command like `pause` it throws out "Unknown command: p" ... i've tried with double quotes, single quotes, no quotes.. seems -a is broken for me.



edit: i just tried passing `gnome-terminal -e <*script*>` to at, and it worked! .. but it's still a bother, because i'd need X running for this to work =\
edit: hmm.. thought i'd give screen a shot, but it was no go for screen

---

