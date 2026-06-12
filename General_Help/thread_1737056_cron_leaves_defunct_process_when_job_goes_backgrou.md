---
title: "cron leaves defunct process when job goes background"
date: 2011-04-23
forum: General Help
---

### Post by shadowlmd on 2011-04-23
I'm using cron to run a tunnel. It is a looped script which never exits, and thats why I don't want cron to wait for it. This is a crontab entry:

@reboot $HOME/cron/portfw.sh &

When I run it manually, everything is ok. But when cron runs it, a defunct sh process keeps running until portfw.sh and it's child are killed. Somehow cron knows that processes spawned in background and keeps waiting for them and ignoring the fact that parent process exited. I tried using setsid to change spawned process group, but it did not full cron, it still knows about child processes.

Is it possible to work it around somehow?

---

### Post by DaithiF on 2011-04-23
Hi, cron doesn't wait for jobs to complete, it launches them in the background anyway so the & is not necessary.  Its probably not doing any harm either, but I suggest you remove it.

I don't think I understand exactly what the issue is.  Are you saying that in addition to the portfw.sh script that cron also launches another (related) process?  maybe you can explain again, give more details.

---

### Post by shadowlmd on 2011-04-23
You are wrong. Cron does wait for all jobs to complete, this is how it looks like:


```
STAT  EUID  RUID TT       TPGID  SESS  PGRP  PPID   PID %CPU COMMAND
Ss       0     0 ?           -1   800   800     1   800  0.0 cron
S        0     0 ?           -1   800   800   800   813  0.0  \_ cron
Ss    1000  1000 ?           -1   834   834   813   834  0.0      \_ sh
S     1000  1000 ?           -1   834   834   834   838  0.0          \_ portfw.sh
S     1000  1000 ?           -1   834   834   838   848  0.0              \_ ssh
```If I add & to command line, portfw.sh gets reparented to PID=1 and sh (PID=834) gets defunct. And remains in this state until processes 838 (portfw.sh) and 848 (ssh) killed. Only after that, cron process (PID=813) exits and defunct sh (PID=834) vanishes.

I want only portfw.sh and it's child ssh remained in memory after being launched by cron, and spawned cron process (PID=813) gone.

---

### Post by DaithiF on 2011-04-23
> **shadowlmd said:**
> You are wrong. Cron does wait for all jobs to complete, 
No it doesn't actually.  **Wait for jobs to complete **implies that if cron runs a job which runs forever, that cron will block and wait for that job ... ie. that cron won't run subsequent cron jobs because its waiting for the first.  And thats not the case. 

I think you mean that the cron daemon is the ultimate parent of the child processes that comprise the cron job that gets executed, and yes that is correct.  And I see that your use of '&' does result in that job getting assigned to a parent pid of 1 rather than cron, so I understand now what you are trying to do.

Rather than wrestle with how cron spawns child processes, why not use /etc/rc.local -- its a better way for launching a daemon process than cron's @reboot mechanism for exactly this kind of reason.

---

### Post by shadowlmd on 2011-04-23
> **DaithiF said:**
> No it doesn't actually.  **Wait for jobs to complete **implies that if cron runs a job which runs forever, that cron will block and wait for that job ... ie. that cron won't run subsequent cron jobs because its waiting for the first.  And thats not the case.
I know that. I mean, spawned cron process waits for job to complete and sends mail if something was sent to stdin/stderr, or job was killed. I don't want all of that.

> Rather than wrestle with how cron spawns child processes, why not use /etc/rc.local -- its a better way for launching a daemon process than cron's @reboot mechanism for exactly this kind of reason.
I don't have root rights. And it's still interesting, how cron knows about spawned process' children? I used setsid to change sid/ppid of spawned process that goes to background. It should be impossible to detect such process as a child, but still cron does that somehow.

---

### Post by shadowlmd on 2011-04-23
In more details, lets have some examples.

Lets have something like this in /path/to/portfw.sh:
```

#!/bin/bash

setsid /path/to/realscript.sh &

```

Lets have something like this in /path/to/realscript.sh:
```

#!/bin/bash

while true; do
  sleep 10
done

```

And finally, lets put it in crontab:
@reboot /path/to/portfw.sh

It should work like this:
1. Cron launches /path/to/portfw.sh
2. /path/to/portfw.sh launches /path/to/realscript.sh in background, changes it's sid/ppid to it's pid, and then exits.
3. Cron detects that /path/to/portfw.sh exited without error and exits too.

But instead on step 3 cron ignores that /path/to/portfw.sh exited and keeps waiting for /path/to/realscript.sh to exit.

---

### Post by DaithiF on 2011-04-26
I can reproduce this issue in 10.04 but not in 10.10.  There were some changes between to the two to the fork behaviour for child processes (calls to fork replacing vfork).  Can you try on 10.10?

---

### Post by shadowlmd on 2011-04-26
I can confirm this doesn't happen in 10.10. Any hope it will be fixed in 10.04?

---

### Post by DaithiF on 2011-04-26
I doubt it :)  Other than the zombie process sticking around theres no particularly bad consequences from this so I doubt much appetite for backporting the later cron version to 10.04 .  You can always try though ... ie. raise a bug in launchpad.

Or just try updating your 10.04 machine with the binary from 10.10 ... i imagine it should work fine.

---

### Post by shadowlmd on 2011-04-26
Just submitted a bugreport. Thanks for help.

---

### Post by DaithiF on 2011-04-26
Did some experimenting, heres what I think is happening, and why the problem doesn't exist in 10.10:

First setting out some background so we can agree on what we call the various processes involved.  For each crontab entry the cron daemon forks itself, and this middle process then forks itself again to run the crontab command (and maybe also a mail command if MAILTO is set)

so the command hierarchy is:
cron   # this is the top level cron daemon
    CRON      # lets call this the middle process
         sh -c "your command here"   # this is the grandchild process

in your case "your command" runs a script which in turn runs another (backgrounded) process.

The middle process opens 2 pipes to the grandchild so that it can (a) write any command line args specified in the crontab entry to the grandchild, and (b) so that it can read the stdout/stderr output of the grandchild (for eventual mailing to the user).  We can ignore (a) because cron will close this itself once it has written to it.  But I think your issue is caused by (b) ... the grandchilds stdout/stderr (and that of any child processes it runs) is a pipe to the middle process, and unless/until that pipe is closed, the middle process cannot exit.

In the version of cron shipped in 10.10 the stdout/stderr pipe from middle process to grandchild has been replaced with a tempfile (this was to fix some timeout issue with long running processes I believe).  The fact that a child run by the grandchild may continue writing to a tempfile (as opposed to a pipe) isn't significant at the O/S level, the middle process will happily exit once the grandchild has completed, regardless of what else may have a stdout/stderr pointing to this tempfile.

If this is correct, then if you explicitly close the stdout/stderr file descriptors in your 1st level script, then this will close the pipe and allow the middle process to exit.

In other words, add:
```
exec 1>&-
exec 2>&-

```to your script before you run your setsid child process and your defunct sh process and middle cron process should terminate ok.

---

### Post by DaithiF on 2011-04-26
and in case the above wasn't clear, regarding this point in your earlier post:
> 
I used setsid to change sid/ppid of spawned process that goes to  background. It should be impossible to detect such process as a child,  but still cron does that somehow. 	

I think it is the open pipe that ties the backgrounded setsid'ed process to the parent.

cheers

---

### Post by DaithiF on 2011-04-26
also worth noting that this isn't really a cron issue therefore.  Because if you're running a script as a daemon then its really the responsibility of that script to insulate itself from its environment so that it can truly run as a daemon, e.g. like in this case closing any open pipes to a parent so that it is running standalone from other processes.

so in summary your wrapper script should close the file descriptors, then run its child command with its output redirected to a file, or wherever else you may choose (e.g /dev/null, etc)

---

### Post by shadowlmd on 2011-04-26
> **DaithiF said:**
> so in summary your wrapper script should close the file descriptors, then run its child command with its output redirected to a file, or wherever else you may choose (e.g /dev/null, etc)
Thank you very much for research and help! This indeed worked like a charm. :)

---

### Post by DaithiF on 2011-04-26
You're welcome.  For the sake of good order would you mind closing the launchpad bug you opened?

thanks

---

### Post by shadowlmd on 2011-04-26
Yeah, of course.

---

