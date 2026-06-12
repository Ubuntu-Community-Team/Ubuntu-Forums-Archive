---
title: "Screen with start command"
date: 2011-11-20
forum: General Help
---

### Post by jfreak53 on 2011-11-20
I am trying to run screen with a command immediately and not SHOW the screen to the user running.  In other word's start it with the command and that's it.

This is what I try:

> screen -A -m -d -S "mine" /home/user/run.sh

I want it to start a new session, then run that shell script and just run it.  I want to invoke that screen command from cron for a user.

When I run it, it just exists and does nothing, the command doesn't run the session is not started.  If I run screen -ls there are no session's.

But if I run:

> screen -A -m -d -S "mine" bash

That works just how I want it to.  What gives?  I just want to run screen and have a command start immediately in that new named session.  Any thoughts?

I'm using Screen version 4.00.02 (FAU) 5-Dec-03

---

### Post by Toz on 2011-11-20
Is the file /home/user/run.sh executable? I created the same file on my system, made it exectable and the command worked.

```
$ ls -l run.sh 
-rwxrwxr-x 1 toz toz 18 2011-11-20 13:11 run.sh

$ cat run.sh 
#!/bin/bash
bash

$ screen -A -m -d -S "mine" /home/toz/run.sh

$ screen -ls
There is a screen on:
	20279.mine	(11-11-20 01:11:37 PM)	(Detached)
1 Socket in /var/run/screen/S-toz.


$ screen -v
Screen version 4.00.03jw4 (FAU) 2-May-06
```

---

### Post by jfreak53 on 2011-11-20
Hmm, yeah it is X, that's wierd.  Yeah I just ran ls -l and it has x plus I run this command from the cli all the time and it works just fine.

Hmm.

---

### Post by Toz on 2011-11-20
Can you share the contents of your run.sh? Maybe its something in there that's preventing it from running from within a screen session.

---

