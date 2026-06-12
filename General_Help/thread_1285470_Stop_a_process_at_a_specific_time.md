---
title: "Stop a process at a specific time"
date: 2009-10-07
forum: General Help
---

### Post by stefanadelbert on 2009-10-07
If I want to start a task at a specific time and then want that task to exit at a specific time (equivalent of Ctrl+C). I can easily start the task in crontab, but getting it to stop is the problem. Maybe I could grab the PID and then kill it, but that seems clunky.

What would be the best way to do this?

---

### Post by Slim Odds on 2009-10-07
It depends on what types of signals the program respects (handles).

```
kill -l
``` will list the types of signals available. You'll have to check the application to see which one to use.

Then you use:```
kill -<SignalName> <PID>
```

---

### Post by stefanadelbert on 2009-10-07
Is there a better way to get a PID for a process than "ps | grep xxx | awk"?

---

### Post by Slim Odds on 2009-10-07
> **stefanadelbert said:**
> Is there a better way to get a PID for a process than "ps | grep xxx | awk"?

There is a command called 'killall' that kills by name. You might want to read the man page.

---

### Post by Anarci on 2009-10-07
Close, when a process is started the terminal returns its pid - if you save this pid you can use it later to terminate the process.

This threads explains in more detail - [http://ubuntuforums.org/showthread.php?t=530553](http://ubuntuforums.org/showthread.php?t=530553)

---

### Post by stefanadelbert on 2009-10-07
Similar to the thread quoted by Anarci, I need to be able to run multiple instances of a program and the stop specific ones at particular times, preferably all with crontab.

pidof returns all PID's for all intances of a program, which is new command to me and a nice one! But not immediately useful at this point, in the same way that killall is not useful.

Looks like I'm going to need to do some work to store PID files in /var/run, but only root has "rw" and the user that needs to run the program should not have root access. I could store PID files elsewhere (user's home), but then the solution starts becoming hacky, right?

---

### Post by Slim Odds on 2009-10-07
> **Anarci said:**
> Close, when a process is started the terminal returns its pid - if you save this pid you can use it later to terminate the process.

Good point. I forgot about that one...... :(

---

### Post by Anarci on 2009-10-08
It can be hacky or not depending on how you script it. Only root is allowed to write to /var/run for security reasons - you could chown a directory for yourself in /var/run and then save all your .pid files there but this isn't much better than just storing them in your home directory or any less hacky ;).

---

### Post by stefanadelbert on 2009-10-13
The process that I want to run doesn't seem to populate $! with its PID unless it's run in a particular way - by using the --foreground argument to force it to run in the fg. 

I've managed to get it working by storing the PID from $! after starting the process in the fg and putting the PID in a pid file in a subfolder within /var/run with the correct permissions for the non-root user. I can then kill just the process that I need to kill rather than unwittingly taking down other instance of the same process with a brute force killall.

Shell special variables are your friends. Thanks for the help.

---

