---
title: "How to properly shut down system remotely with SSH?"
date: 2010-04-21
forum: General Help
---

### Post by NTolerance on 2010-04-21
So I've got a backup server that has a daily cronjob to back up all my systems.  My desktop PC is usually in sleep mode to save power.  So my backup server has to wake up the desktop via wake-on-LAN to start the backup job.  When the backup script is done, my backup server sends a shutdown command to the desktop to put it back in sleep mode.

The trouble is that SSH is timing out during the shutdown process and waits a ridiculous amount of time before giving up and allowing my backup server to move on to the next backup script.  Here's the portion of my backup script for the desktop that does the shutdown stuff:

```
ssh user@host.lan '/usr/bin/shutdown -p +1'
```

Here's what cron sends me via e-mail:

```
Read from remote host host.lan: Connection timed out

real    164m46.280s
user    5m16.160s
sys     1m39.760s
```

Normally the entire backup job will only take about 5 minutes.  But because of SSH timing out, it takes 164 minutes!  

As a matter of detail, my backup server is running Ubuntu 9.10, and the desktop is Windows 7 x64 with Cygwin.  The -p option for the shutdown command in Cygwin is for sleep mode.

---

### Post by NTolerance on 2010-04-21
I found a solution to my problem.  From the ssh man page:
> -f      Requests ssh to go to background just before command execution.

My new command line:
```
ssh -f user@host.lan '/usr/bin/shutdown -p now'
```

---

