---
title: "cron problem"
date: 2010-05-24
forum: General Help
---

### Post by supradave on 2010-05-24
I'm having a problem that I have not seen before.  I have a simple bash script that I'm calling from cron.  The script works flawlessly from the command-line, be that called by 'bash script' or './script'.

In the script, I put in a few if statements, like

```
if ! [ -d /dir ]
then
  mkdir /dir
fi
```

and when run from cron, the job exits and subsequent commands are not run because the script is exiting at the if statement.  
I've debugged every way to Sunday and cannot figure out what's going on.

The only difference that I have that could be a concern is an
```
su - user -c "service stop"
``` and that that may be returning something untoward.

---

### Post by arrange on 2010-05-24
I don't see any problems based on your explanation. Could you provide more info?
I'd try to pinpoint the problematic line(s) of code or possibly run the script via ```
bash -x /path_to_the_script
```from a) terminal and b) using *cron*. Paste the outputs here or on [Ubuntu pastebin]("http://paste.ubuntu.com/").

---

### Post by CharlesA on 2010-05-24
That looks fine, but we would need to see the entire script to see where the problem lies.

---

### Post by supradave on 2010-05-24
I moved the if's above the execution of the relevant code and that seems to have resolved the problem.  I'm not saying it's solved but it's working.

---

### Post by gmargo on 2010-05-24
> **supradave said:**
> 
```
if ! [ -d /dir ]
then
  mkdir /dir
fi
```

The not("!") is part of the expression, and goes after the test("[") command, not before:
```

if [ ! -d /dir ]
then
    mkdir /dir
fi

```

---

### Post by arrange on 2010-05-25
>gmargo
Are you sure? Aren't they basically the same? For example (in lucid)```
arrange@lucid-lean:~$ grep '\!\ \[' /etc/cron.daily/man-db
if ! [ -d /var/cache/man ]; then
```

---

### Post by gmargo on 2010-05-25
> **arrange said:**
> >gmargo
Are you sure? 
I thought so...:( but I was incorrect; that syntax does work.

---

