---
title: "Cron, at, atd issues"
date: 2009-09-14
forum: General Help
---

### Post by Eltern on 2009-09-14
Crontab isn't working. I've tried various entries such as this:
```
# m h  dom mon dow   command
 2 9   *   *   *    env DISPLAY=:0.0 /usr/bin/amarok

```
And it simply doesn't do anything, even it's writing "HI!" to a temporary log.

Similary, "at" isn't working, either. When I put in a command, it gives this complaint:
```
job 1 at Mon Sep 14 09:06:00 2009
Can't open /var/run/atd.pid to signal atd. No atd running?

```

Thinking these functions may all be related, I rand atd (simply typed "atd" and hit enter). There's no response, and the behavior of crontab and at do not change. Any thoughts? Thanks!

---

### Post by sedawk on 2009-09-14
Running a command that uses DISPLAY from cron might not
work.
Which user is running the cron command (root? desktop user?
Is there any user logged in to the desktop?)?
You can kind of simulate the same behaviour by running
the command from a real text console not started from the
desktop (e.g. use the text consoles at Ctrl-Alt-F1, Ctrl-Alt-F1, ...) or ssh to the local machine "ssh localhost" without
enabling X11 forwarding (you might need to install package
openssh-server to get sshd).

What happens if you try
```

# m h  dom mon dow   command
2 9   *   *   *    env DISPLAY=:0.0 /usr/bin/xterm >/dev/shm/xterm.log 2>&1 

```
Check if /dev/shm/xterm.log reports any problems with
permissions.

If you run 
```

ps -ef |grep atd
[CODE]
can you see that /usr/sbin/atd is running?

I have no problems runnning an at command as the normal
desktop user:
[CODE]
echo "echo hello >/dev/shm/hello.out"|at now + 1 minute

```
works fine here.

---

### Post by Eltern on 2009-09-16
I did a lot of updates to my computer, including getting a new kernel. Now cron and at are working! Yay!

HOWEVER, I finally realized that while booting up, its says that loading crond fails. I've Googled around, but not found any way to correct this. Any thoughts? Right now it's not producing any symptoms, since con is working.

---

