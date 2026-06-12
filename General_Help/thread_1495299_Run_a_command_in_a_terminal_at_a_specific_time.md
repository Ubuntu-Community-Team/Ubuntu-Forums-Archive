---
title: "Run a command in a terminal at a specific time?"
date: 2010-05-27
forum: General Help
---

### Post by Icarus_Complex on 2010-05-27
Hello,
I'm wanting to be able to run a terminal command at a specific time. For example, I would like to install software via apt-get at 4:00 am (for bandwidth reasons, I have hughesnet =[ ).
Any help would be much appreciated! Thanks!

---

### Post by dcstar on 2010-05-27
> **Icarus_Complex said:**
> Hello,
I'm wanting to be able to run a terminal command at a specific time. For example, I would like to install software via apt-get at 4:00 am (for bandwidth reasons, I have hughesnet =[ ).
Any help would be much appreciated! Thanks!

```
man cron
```

---

### Post by Icarus_Complex on 2010-05-27
Wow, thanks.

---

### Post by BoneKracker on 2010-05-27
Cron is for running a command (or a script) at a regular interval (for example, every night at 3:00 am, or on the first day of each month at 7:00 pm).

To run a command once at a predetermined future time, use the command 'at'.  This requires the program 'atd' to be installed on your machine and running.  You start it like any other daemon (service).

Once you're running the daemon in the background, using it is pretty easy.  For example, to set XMMS to play "wakeup.ogg" at 6am tomorrow morning:```
~$ at 6am tomorrow
at> xmms ~/music/wakeup.ogg
at> <Ctrl-D>
job 2 at 2010-5-28 06:00

```
You can list the 'at' jobs you have scheduled with the command 'atq'.  You can remove a scheduled job from the queue with the command 'atrm'.

Also, in addition to scheduling a job for a specific time, you can schedule a job to run when the machine's not busy (when the load drops to a certain point).

To see if it's installed:
```
sudo which atd
```
Here is a man page for the 'atd' daemon.
[http://manpages.ubuntu.com/manpages/hardy/man8/atd.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/atd.8.html)

Once you have it installed, be sure to read the man pages for atd, at, atq, and atrm.



.

---

### Post by Icarus_Complex on 2010-05-28
Thanks, but I do not think it's working. I tried the command 
> at now + 2 minutes
warning: commands will be executed using /bin/sh
at> firefox
at> <EOT>
job 9 at Fri May 28 13:42:00 2010

Just to see if it would work, and nothing happened.

---

### Post by BoneKracker on 2010-05-28
> **Icarus_Complex said:**
> Thanks, but I do not think it's working. I tried the command 

Just to see if it would work, and nothing happened.

I'm not entirely clear this, but I think that's because 'at' doesn't have a login shell.  At any rate, it wasn't really designed to run interactive programs but to start batch jobs that can run in the background.  By default, all output of an at session is redirected (I think stdout is redirected to /dev/null, and stderr is redirected to syslog).

If you want a quick test to see that it works, try this:
```
~ $ at now + 1 minute
at> echo "Holy snappin arsles, it works!" > ~/at.out
at> <CTRL+d>
```

Or try this:
```
~ $ at now + 1 minute
at> shutdown -t 15
at> <CTRL+d>
```

Unless somebody smarter can offer you more insight into what it can and cannot run, you'll just have to experiment.  I only use it to to run command-line stuff.

---

### Post by Icarus_Complex on 2010-05-28
Oh cool, I think I get what you're saying. Thanks!

---

