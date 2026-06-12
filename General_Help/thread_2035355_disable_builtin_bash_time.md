---
title: "disable builtin bash time"
date: 2012-07-30
forum: General Help
---

### Post by hwttdz on 2012-07-30
I'd like time to reference /usr/bin/time instead of the bash builtin, but I can't figure out how to disable "keywords".  Anyone know?

---

### Post by idoitprone on 2012-07-30
> **hwttdz said:**
> I'd like time to reference /usr/bin/time instead of the bash builtin, but I can't figure out how to disable "keywords".  Anyone know?

i will say dont mess around with ubuntu defaults and only change your account's time command

gnu bloat sigh...


just use the command alias

```
alias time='/usr/bin/time'
```

add this line to .bashrc
and it should work

---

### Post by asmoore82 on 2012-07-30
An alias is a nice permanent fix, but I would edit or create "$HOME/.bash_aliases" instead.

For a once in a while, spur of the moment, solution; use a backslash:

```
**$ time**

real	0m0.000s
user	0m0.000s
sys	0m0.000s

**$ \time**
Usage: time [-apvV] [-f format] [-o file] [--append] [--verbose]
       [--portability] [--format=format] [--output=file] [--version]
       [--quiet] [--help] command [arg...]
```

This is a handy trick when you may be on someone else's account or computer.

---

### Post by hwttdz on 2012-07-30
I'm a big fan of simplicity, so yes I can alias time, and aliases get processed before shell keywords before a path search, but I'm just adding more bandaids to the problem.  For instance after aliasing time to ls, type -a gives:

```
time is aliased to `ls'
time is a shell keyword
time is /usr/bin/time
```

I'm wondering if it's possible to disable the shell builtin.  After which "type -a time" should give:

```
time is /usr/bin/time
```

---

### Post by idoitprone on 2012-08-01
i believe it is the enable command

```
enable -n command
```
to disable

[http://ss64.com/bash/enable.html](http://ss64.com/bash/enable.html)

to re enable

```
enable command
``````
man enable
```

---

### Post by hwttdz on 2012-08-03
That's how I overrode the bash kill command, so I tried that.  However I get:

"bash: enable: time: not a shell builtin"

apparently bash differentiates between builtin's and keywords?

Also, the man entry for enable is inside bash's man page.

---

### Post by idoitprone on 2012-08-03
> **hwttdz said:**
> That's how I overrode the bash kill command, so I tried that.  However I get:

"bash: enable: time: not a shell builtin"

apparently bash differentiates between builtin's and keywords?

Also, the man entry for enable is inside bash's man page.

```
which time
```

```
builtin time
```

---

