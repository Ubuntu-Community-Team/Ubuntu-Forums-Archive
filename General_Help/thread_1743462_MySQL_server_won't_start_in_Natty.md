---
title: "MySQL server won't start in Natty"
date: 2011-04-29
forum: General Help
---

### Post by xorand on 2011-04-29
Hi, I installed mysql server 5.1 via synaptic.  It seemed to install as usual.  However, when I type 'mysql' in the console I get:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


ps aux | grep mysql
rick      5474  0.0  0.0   4152   852 pts/0    S+   21:08   0:00 grep --color=auto mysql

sudo service mysql stop

Warning: Fake initctl called, doing nothing.

sudo service mysql start
[sudo] password for rick: 

Warning: Fake initctl called, doing nothing.

Was I too early in moving to Natty?  How can I get MySQL server to start?

---

### Post by millertime113 on 2011-04-30
I am having the exact same problem.  Exact error code and everything.  I just upgraded to natty, which was its own adventure let me tell ya.  I already had mysql installed prior to the upgrade and this error started occurring after the upgrade.  I completely uninstalled anything mysql related with --purge and its still doing it. A quick ps aux revealed it wasn't running after startup, so I started it, verified with ps aux, and it still does it.  I tried starting with mysqld, at the suggestion of several forums I read (I don't really know the difference) and it executes without error, but the error still occurs trying to run mysql.

I've tried everything I can think of and I'm hoping its just a natty error and will be resolved shortly.

---

### Post by bijur on 2011-05-02
It seems to be some kind of problem with the Upstart/init.d scripts.

If you run "mysqld" on the command prompt, it works without problems.

I'm submitting right now this bug to LaunchPad. Let's hope they solve this quickly.

EDIT: The problem was solved with the tip from [http://roggablog.blogspot.com/2011/05/upstart-natty-narwhal-ubuntu-1104-power.html](http://roggablog.blogspot.com/2011/05/upstart-natty-narwhal-ubuntu-1104-power.html)

Just do a "sudo apt-get install upstart --reinstall" and all will go back to normal.

It seems to only happen when you do a "dirty" (meaning "not clean") reinstall of Natty, which was the case of #2 (and myself too) :)

Problem solved.

Cheers,
Daniel

---

### Post by millertime113 on 2011-05-02
Ya I did an upgrade from 10.10 and it completely locked up right at the end. Mouse wouldn't even move.  I finally got my system repaired through recovery and booting after some tweaking.  I tried to reinstall mysql to no avail.  I finally got it working by running apt-get clean to clean the local cache and force re-download from the repos.  I'm guess that possibly due to the servers being slammed from natty release the package got corrupt.  Works perfect now.  

One thing to note, I wasn't getting the 'fake initctl' error.  If I tried to start mysql through 'service mysql start', manually running the init.d script, or with mysqld it would just fail in one way or another.  Manually trying to start service mysql would just give me 'failed to start' while mysqld would give something about permissions.

---

### Post by Ricalsin on 2011-05-05
I'm not getting the same love:  "service mysql start" gives me:

```
 start: Rejected send message, 1 matched rules; type="method_call", sender=":1.94" (uid=1000 pid=9695 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
```Same 10.04 upgrade to 11.04 nightmare.  Locked up at the very end with "reloading installed packages" and never installed any of them.  Created a CD, re-installed and started from scratch.  Ouch.  

I'm still just trying to get the myphyadmin to show.  Any other suggestions or links?

EDIT: Okay, my fault.  Using bad commands.  The advice above (Millertime and bijur) proved to be the solution for me too.  Thanks!

---

### Post by lifeLogic on 2011-08-02
Greetings, 
Thank you for making this thread.  It helped me a lot ! 
Especially the message quoted below made by bijur.  
The solved my problem !

I did a fresh install of Ubuntu 11.04.  Then, I tried to insall MySQL and I kept getting 
error messages when I tried to log in.  But, the below fixed it.  

> **bijur said:**
> 

EDIT: The problem was solved with the tip from [http://roggablog.blogspot.com/2011/05/upstart-natty-narwhal-ubuntu-1104-power.html](http://roggablog.blogspot.com/2011/05/upstart-natty-narwhal-ubuntu-1104-power.html)

Just do a "sudo apt-get install upstart --reinstall" and all will go back to normal.

It seems to only happen when you do a "dirty" (meaning "not clean") reinstall of Natty, which was the case of #2 (and myself too) :)
l
Thanks everyone.
Cheers!

---

