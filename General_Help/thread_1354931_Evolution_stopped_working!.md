---
title: "Evolution stopped working!"
date: 2009-12-14
forum: General Help
---

### Post by DavidS on 2009-12-14
I have used Evolution for a long time - currently under Ubuntu 9.04.  Today, it won't launch properly: it gets as far as drawing the screen and saying "Loading..." against the main folders.  Then it seems to crash, and has to be killed.

It doesn't appear to be a server problem, because I can access the IMAP server from my iPhone without any problem.

I have tried reinstalling Evolution (and most of the associated packages) but without any improvement.

If I run 'evolution' or 'evolution --component=mail' from a terminal, I get the following output:

evolution-shell-Message: Killing old version of evolution-data-server...
** (evolution:7325): DEBUG: mailto URL command: evolution --component=mail %s
** (evolution:7325): DEBUG: mailto URL program: evolution
** (evolution:7325): DEBUG: EI: SHELL STARTUP

And that's as far as it gets.

The only thing I have done that might have affected it was to run "Computer Janitor", but as that only removed a lot of supposedly redundant installation files, it's hard to see how it could have caused this problem.

Any helpful suggestions will be gratefully received!

David

---

### Post by DavidS on 2009-12-14
The problem is solved: Evolution is now working normally.  The reason?  No idea!

---

### Post by DavidS on 2010-01-10
That was in December.  Today - exactly the same thing is happening.  Output at a terminal is also exactly as reported before.

Can anyone help on this problem, please?

David
:(

---

### Post by slob_2006 on 2010-01-10
I have the same problem. Evolution has been working perfect since clean install of Karmic. After a regular update yesterday, which installed kernel 2.6.31-17, evolution now freezes on startup. Also attempting to click date/calendar and Applications/Places/System in top gnome panel does not respond. 

My only workaround at the moment is to boot using kernel 2.6.31-16 in grub, which I had not removed yet. Everything seems to work with this.

Any ideas ... anyone????

---

### Post by hughcrowther on 2010-01-12
Me too - request for mail & send, just keeps turning and then goes grey and I have to force quit

---

### Post by howefield on 2010-01-12
> **DavidS said:**
> That was in December.  Today - exactly the same thing is happening.  Output at a terminal is also exactly as reported before.

How did you fix it 4 weeks ago ?

You also need to be very careful with computer janitor, don't just trust that what it thinks are redundant files are actually redundant files. Make sure you are happy with what it is proposing before committing.

---

### Post by VitalBodies on 2010-01-14
Did you try this at the terminal:
```
gdb evolution
```
Then 
```
run
```
Evolution will start and you can watch the terminal for errors. 
If it crashes try this command for a back trace. 
```
(gdb) thread apply all bt
```

Also, does Evolution unfreeze if you reconnect to the internet? 

My Evolution worked great until I unplugged the external USB hard drive (Ubuntu 9.10) and plugged it into a different/new computer. 
Everything but the xsensors and evolution worked great. 
So I reloaded the new computer with a fresh vanilla install of Ubuntu 9.10 and same thing? When it hangs I get a broken pipe. Although reconnection to the internet brings Evolution back to life. I used to force it to quit but I do not need to, I just re-connect. Still, it should not be freezing. Someone on another thread claims they fixed the issue by renaming the .evolution folder in the home/user-name-goes-here and restarting evolution. Anyone tried that or figured this out? 
I get a lot of these: (although I am not so sure they are causing the problem.)
```
CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
```

---

### Post by DavidS on 2010-02-02
I booted the computer this morning, and once again had the same problem.  But by killing all running processes with names which included 'evolution', I found that Evolution started again without a problem.

I don't know why the problem occurred in the first place, but I think this is the solution I used on previous occasions.  Hope it helps someone!

In more detail:

When Evolution is running, then 'ps -A | grep evolution' normally shows 4 processes: evolution, evolution-data-server-2.28, evolution-exchange-storage, and evolution-alarm-notify.

If you issue the command 'kill' followed by the relevant process numbers - e.g.
kill 3591 3597 3601 3631
Then it should stop all those processes.  Check again, though, with
ps -A | grep evolution
because I have found that one of the processes (evolution-alarm-notify, I think) sometimes gets restarted.

If you find that any of the processes refuses to be killed with the usual "TERM" signal, then use "KILL" by adding '-9' after the command 'kill', e.g.
kill -9 3591

After killing all these evolution processes, you will (I hope) find as I did that Evolution starts normally.

Unfortunately I can't retest any of this, because I find that when Evolution is running OK, as it is now, then closing it does leave 3 processes running, but nonetheless the main Evolution program can be restarted without any problems.  So what actually causes these occasional hang-ups is still a mystery.

David

---

### Post by VitalBodies on 2010-02-03
So are saying that Evolution merely starts ok, or that that it no longer hangs/freezes/crashes after it is started?

---

### Post by Vevmesteren on 2010-03-24
```
-desktop:~$ evolution
** (evolution:2844): DEBUG: mailto URL command: evolution %s
** (evolution:2844): DEBUG: mailto URL program: evolution

** (evolution:2844): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Segmentation fault

```

is what I get when trying to run my evolution since today. It started with me wanting to pull some emails of my IMAP server into a local Evolution Directory. Every time I tried that Evolution would crash on me. Then since this evening Evolution won't start anymore due to the rather cryptic reason above. 

I did try killing all Evolution Processes as described above without any luck. 

killing all processes and trying again turns out this in the terminal :
```

-desktop:~$ evolution
** (evolution:2922): DEBUG: mailto URL command: evolution %s
** (evolution:2922): DEBUG: mailto URL program: evolution

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2922): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Segmentation fault

```

Karmic with kernel - 2.6.31-20 - 64-bit


Help?

---

### Post by VitalBodies on 2010-03-24
I switched to Kmail. 
In Evolution I did figure out that I could just reconnect to the Internet and it would unfreeze. Additionally that the issue was because of a password keyring problem. Never did figure out how to create the missing group-mail it was looking for.  I had to just switch from Evolution to Kmail. If you figure it out let me know the answer...

Gnome Evolution Keyring: [http://ubuntuforums.org/showthread.php?t=1427723](http://ubuntuforums.org/showthread.php?t=1427723)

Evolution Bug: [http://www.uluga.ubuntuforums.org/showthread.php?p=8948355](http://www.uluga.ubuntuforums.org/showthread.php?p=8948355)

Gnome Evolution Bug: [https://bugzilla.gnome.org/show_bug.cgi?id=606149](https://bugzilla.gnome.org/show_bug.cgi?id=606149)

---

### Post by dcstar on 2010-03-24
> **Vevmesteren said:**
> ```
-desktop:~$ evolution
** (evolution:2844): DEBUG: mailto URL command: evolution %s
** (evolution:2844): DEBUG: mailto URL program: evolution

** (evolution:2844): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Segmentation fault

```

is what I get when trying to run my evolution since today. It started with me wanting to pull some emails of my IMAP server into a local Evolution Directory. Every time I tried that Evolution would crash on me. Then since this evening Evolution won't start anymore due to the rather cryptic reason above. 
..........
Karmic with kernel - 2.6.31-20 - 64-bit


Create a new user and see if Evolution behaves ok, or report it as a bug or search for an existing bug and see what is happening with it.

---

### Post by wolfgang.rumpf on 2010-06-15
Same problem here - Evolution won't start (Lucid Lynx, latest builds of everything).  I grep a ps -el to find all evolution processes, kill them all.  THEN it starts up normally - but WITHOUT the evolution-alarm-notify process!  Any ideas?  I know I could write a script to automate this but maybe the developers can figure this out for real?

> **DavidS said:**
> I booted the computer this morning, and once again had the same problem.  But by killing all running processes with names which included 'evolution', I found that Evolution started again without a problem.

I don't know why the problem occurred in the first place, but I think this is the solution I used on previous occasions.  Hope it helps someone!

In more detail:

When Evolution is running, then 'ps -A | grep evolution' normally shows 4 processes: evolution, evolution-data-server-2.28, evolution-exchange-storage, and evolution-alarm-notify.

If you issue the command 'kill' followed by the relevant process numbers - e.g.
kill 3591 3597 3601 3631
Then it should stop all those processes.  Check again, though, with
ps -A | grep evolution
because I have found that one of the processes (evolution-alarm-notify, I think) sometimes gets restarted.

If you find that any of the processes refuses to be killed with the usual "TERM" signal, then use "KILL" by adding '-9' after the command 'kill', e.g.
kill -9 3591

After killing all these evolution processes, you will (I hope) find as I did that Evolution starts normally.

Unfortunately I can't retest any of this, because I find that when Evolution is running OK, as it is now, then closing it does leave 3 processes running, but nonetheless the main Evolution program can be restarted without any problems.  So what actually causes these occasional hang-ups is still a mystery.

David

---

### Post by wolfgang.rumpf on 2010-06-15
Where exactly do we report this as a bug?

> **dcstar said:**
> Create a new user and see if Evolution behaves ok, or report it as a bug or search for an existing bug and see what is happening with it.

---

### Post by JabberWalkie on 2011-02-20
I also had this problem. I can confirm that killing all evolution related processes seems to have worked, but I am not sure how to reproduce in order to make a bug report. Maybe it has something to do with evolution being improperly shutdown in the first place.....

---

