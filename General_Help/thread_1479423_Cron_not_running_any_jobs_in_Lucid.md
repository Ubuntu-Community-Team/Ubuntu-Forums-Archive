---
title: "Cron not running any jobs in Lucid"
date: 2010-05-10
forum: General Help
---

### Post by Eltern on 2010-05-10
I use crontab for a daily alarm clock, which stopped working after I moved to Lucid. 

```
$ crontab -l
# m h  dom mon dow   command
50 7 * * * /home/jeff/alarm.sh

```

In an effort to demonstrate that cron wasn't running **anything**, I tried this:

```
$ crontab -l
# m h  dom mon dow   command
*/1 *   *   *   *   /usr/bin/gedit

```

Which didn't run anything ever. 

Looking at some of the concepts described [here]("http://aplawrence.com/Unixart/crontab_not_running.html"), I next looked at if crontab was being read.

```
$ ls -lut /etc/crontab
-rw-r--r-- 1 root root 724 2010-05-10 11:02 /etc/crontab

``` 
11:02 is about when I turned on the computer, and long before many edits to the crontab file.

When did cron run, though?
```
$ ls -lut /etc/init.d/cron
lrwxrwxrwx 1 root root 21 2010-05-10 14:35 /etc/init.d/cron -> /lib/init/upstart-job

```

That's after I turned on the computer, but what's this upstart-job business? I know upstart is something Ubuntu has started to use, but I know nothing about it.

I also tried reassigning the crontab file with "crontab -u jeff new-crontab-file", but it didn't change any behavior.

Thoughts? Thanks!

---

### Post by bredman on 2010-05-10
I assume you are using sudo crontab -e to edit the crontab file...

Have you checked if cron is still running?
ps aux|grep cron

Check if cron is mentioned in any log files
grep -r 'cron' /var/log

Your gedit test might not work because it is interactive. Try something like
*/1 * * * * /bin/date >> /test.txt

---

### Post by Eltern on 2010-05-10
Ah! I forgot "export DISPLAY=:0 &&"! Thanks.

For future people who find this post, you need it to look something like this:

```
$ crontab -l
# m h  dom mon dow   command
32 22 * * * export DISPLAY=:0 && /home/jeff/alarm.sh

```

More information [here]("http://ubuntuforums.org/archive/index.php/t-185993.html").

---

### Post by dcstar on 2010-05-11
> **Eltern said:**
> Ah! I forgot "export DISPLAY=:0 &&"! Thanks.

For future people who find this post, you need it to look something like this:

```
$ crontab -l
# m h  dom mon dow   command
32 22 * * * export DISPLAY=:0 && /home/jeff/alarm.sh

```

More information [here]("http://ubuntuforums.org/archive/index.php/t-185993.html").

Then mark the thread.

---

### Post by grenobel on 2010-05-11
The display export does not explain why cron jobs are not running. I am having the problem of cron absolutely not working  *only since upgrading to Lucid*. To see if cron was working or not, I added a cron job to /etc/crontab:

```
*/5 * * * * root /bin/echo 3 > /proc/sys/vm/drop_caches
```

Memory cache is not changed, so that didn't work. Next I tried adding the same thing via "crontab -e", also with no luck. 

Just to be sure I wasn't losing it, I tried this as well - still no luck.

```
* * * * * root /usr/bin/touch /root/crontwatch.txt
```

File does not even generate.
Yes - cron is running:

```

root@glebel:/etc/init# ps aux | grep cron | head -1
root     10221  0.0  0.0   3836  1008 ?        Ss   08:44   0:00 cron

```


I admit I know nothing about upstart. So I read the screen and follow the output:

```

root@glebel:/etc/init# /etc/init.d/cron status
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cron status

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the status(8) utility, e.g. status cron
cron stop/waiting
root@glebel:/etc/init# status cron
cron stop/waiting

```

I have no clue as to what I need to do to get cron to actually work. I read your post, about the console - but since neither of these have anything to do with a display, I just wanted to find out if there is some magic to getting cron functionality back. The same cron entries work in both via "/etc/crontab" as well as with "/usr/bin/crontab -e" on my laptop which is still running Hardy and init.d scripts. 

Any pointers for an upstart clueless noob?

---

### Post by grenobel on 2010-05-12
I've been searching around in the forums. A lot of issues with cron on Lucid, but no real answers. 
Also searched around on 'the google', but no good responses either... 
Is it possible to *NOT* use upstart in Lucid?

---

### Post by sedawk on 2010-05-12
> **grenobel said:**
> 
```
* * * * * root /usr/bin/touch /root/crontwatch.txt
```

Okay, that syntax is okay for /etc/crontab, but I actually
never used that one.
When running "crontab -e" to edit a crontab you should
be editing a crontab file that doesn't need the user name.
So the input line for "crontab -e" should be
```
* * * * * /usr/bin/touch /root/crontwatch.txt
```

But I'm not sure that is the root cause for all the trouble ...

I never changed /etc/crontab and I just did
a "crontab -e" for the default user (not root) and
the touch worked fine (/home/myuser/cron_is_working.out)

---

### Post by rnjn.sinha on 2010-05-13
cron is not working for me as well after upgrading to Lucid. I was running a script using cron and my crontab looks like the following 

> 
rsinha@Noi1-501465:src$ crontab -l
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h  dom mon dow   command
0 0  * * 2-6 perl /home/rsinha/Work/EDP/Scripts/makedoc.pl


I can see that it has successfully created an entry in /var/spool/cron/crontabs

> 
root@Noi1-501465:/var/spool/cron/crontabs# ls
rsinha
root@Noi1-501465:/var/spool/cron/crontabs# cat rsinha 
# DO NOT EDIT THIS FILE - edit the master and reinstall.
# (/tmp/crontab.YynauE/crontab installed on Tue May 11 09:57:13 2010)
# (Cron version -- $Id: crontab.c,v 2.13 1994/01/17 03:20:37 vixie Exp $)
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h  dom mon dow   command
0 0  * * 2-6 perl /home/rsinha/Work/EDP/Scripts/makedoc.pl


I can also confirm that cron is indeed running on the system

> rsinha@Noi1-501465:cron$ ps aux | grep cron
root       964  0.0  0.0  21068   912 ?        Ss   May10   0:00 cron


---

### Post by tonymaro on 2010-05-17
I'll throw a me-to at this, along with the following notes:

The cron daemon is not automatically starting on a reboot, despite being told to do so.  If I manually start it then it will stay running.  There's no log entry of it even attempting to start when the machine boots.

If I manually start the daemon at each boot, it appears to work as long as there's a bang line at the top of whatever script I run.  For instance, first line of #!/bin/sh in the script.

This is a fresh install (not upgrade) of Lucid.

The cron package is installed by default, but appears non-functional.

---

### Post by OobNosferatu on 2010-05-26
me three!!!

---

### Post by yanewby on 2010-06-09
me four!!!!

---

### Post by owf on 2010-07-06
Me five. How the heck did a bug like cron not working get through?

---

### Post by hysterix` on 2010-07-15
My cron is failure as well and this is literally the last straw with me and ubuntu.

I loved ubuntu 8.04, 8.01 less, 9.04 even less, 9.01 even less, 10.04 even less; I see a pattern emerging.

How the hell could there be a bug in cron, or in somehow the way things are being executed by cron.  Madness, simply madness canonical.

Proxychains program no longer works even though I've compiled from source and done lot's and lots of tricks to try to get it to function.

Practically every single start up process no longer starts up after upgrading to lucid.  I've tried doing a myriad of fixes to no avail, I can't get apache to start up after a reboot after "upgrading" (lol upgrade of number, downgrade of quality) to lucid.

Ubuntu, I'm officially saying this on your own forums for the world to see.  You used to be stable around 8, you used to be cool.  What happened?  Why is canonical releasing such unstable crap?  Is it my fault for upgrading?

Pretty much I have two courses of action seeing as how lucid is pretty much unusable.  I am either downgrading waaaaay back to 8.04 when things worked and were stable, or switch os's.

I think I am going to go with the latter seeing as how things are getting worse and worse and not better.

Ubuntu, I used to be your biggest fan; but now you suck; I'm sorry but if I don't say it, I don't think anybody else will.

Hey canonical, instead of worrying about the next fancy name, or the next set of artwork for the next crap release, how about making the os stable, like, oh I don't know, MAKING SURE GOD DAMN CRON WORKS?!?!?!?!??!?!?!?!?!??!?!  Change your name to comical, because that's what this latest version of your os is, a ****ing joke.  Again, this is from someone who USED to support ubuntu, take this for what its worth.

---

### Post by sgosnell on 2010-07-15
I don't know why, but cron works fine for me.  Just to make sure, I edited my crontab file to touch a file every minute, and it does that, and it also runs whatever else I put in the file.  Something has to be causing the problems mentioned above, but I have no idea what is doing it.  If cron were completely broken, I would think there would have been a loud outcry everywhere, but half a dozen or so isn't that many, as percentages go, and I suspect there has to be some other common problem.

---

### Post by monomox3000 on 2010-07-18
Me six.  Cron was running perfectly until I updated to Lucid Lynx.

---

### Post by monomox3000 on 2010-07-18
I've been trying to solve this, without much sucess

I used
```
ps aux | grep cron
```to check if cron was running... it wasn't

I ran cron as a superuser and it worked

so now I've reduced my problem to figuring out how to make lucid lynx to start cron automatically at boot
so I tried the following command
```
update-rc.d cron defaults
```but got this suspicious output
```
update-rc.d: warning: /etc/init.d/cron missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/cron ...
   /etc/rc0.d/K20cron -> ../init.d/cron
   /etc/rc1.d/K20cron -> ../init.d/cron
   /etc/rc6.d/K20cron -> ../init.d/cron
   /etc/rc2.d/S20cron -> ../init.d/cron
   /etc/rc3.d/S20cron -> ../init.d/cron
   /etc/rc4.d/S20cron -> ../init.d/cron
   /etc/rc5.d/S20cron -> ../init.d/cron
```who knows what that means, but since it has the word "warning" I wasn't sure it was going to work.... 

so I thought I could use the Startup Applications Preferences GUI (under System>Preferences) to add "cron" to the list... it didn't work, 
I also added /usr/sbin/cron to /etc/rc.local, to no avail

---

### Post by jimfcarroll on 2010-07-21
This is absurd! I'm having the same problem.

However, I have one machine that I upgraded and another machine that I installed 10.04 directly on. The one I updated has cron running at startup but I can't seem to figure out how since there are no rc?.d links to the init.d/cron script.

Is this "upstart-job" a linux thing, or an Ubuntu addition to solve a problem that no one had before?

EDIT: Noticed the upstart description given here: [http://ubuntuforums.org/showthread.php?t=1351501](http://ubuntuforums.org/showthread.php?t=1351501) (post #4). Also look at 'man 5 init'. I haven't fixed it yet but just an FYI

---

### Post by jimfcarroll on 2010-07-21
EDIT: Sorry - this post was initially a mistake on my part.

---

### Post by jimfcarroll on 2010-07-21
There's appears to be a state management issue in upstart. I'm not sure what's going on but if I run:

```

sudo service cron stop

```... I get the error message "unknown instance" (since cron is not running) but on a subsequent reboot "cron" seems to autostart.

If I reboot again, however, cron will not be running - unless, prior to rebooting, I run the (seemingly pointless) "stop" again.

Any suggestions?

EDIT: Actually, after having stopped the job by hand, it seems to be managing it correctly now.

---

### Post by jimfcarroll on 2010-07-21
Well,

I managed to get cron consistently running at startup but, if it's what I suspect, then an OS crash or hard power shutdown will restart the issue.

I think upstart is not managing the state correctly. If you manage to shut down your computer without cleanly stopping cron (like, for example, pull the plug), then it will refuse to autostart cron the next time around. You can recover from this state by:

1) Running: 'sudo service cron stop' and ignoring the message.
2) Reboot
3) cron will now be running. So stop it again. This time you should get a clean stop.
4) Reboot

Hopefully the Ubuntu team can repeat this bug now and resolve it.

---

### Post by monomox3000 on 2010-07-23
thanks jimfcarroll, I was getting frustrated that no one else was looking at this problem
I'll try your suggestion
still, there seems to be a bug, how do we get the developers to listen to us?

---

### Post by jimfcarroll on 2010-07-23
There's a bug report already filed at Launchpad. I added my description and linked to this thread. I'm not sure what else to do. It seems pretty major to me.

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/592114](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/592114)

Let me know if the same procedure I went through resolves it for you.

---

### Post by monomox3000 on 2010-07-23
no, your solution doesn't work for me
I haven't been able to stop cron:

```
root@frau-bulap:~# cron stop
cron: can't lock /var/run/crond.pid, otherpid may be 2483: Resource temporarily unavailable
``````

root@frau-bulap:~# service cron stop
stop: Unknown instance: 
```One of your posts says [SOLVED]... I don't know who marked it a such, but I don't think this problem has been solved... 

Thanks, though

---

### Post by jimfcarroll on 2010-07-24
Yes. Use the "service" wrapper and ignore the "Unknown instance." Then reboot and run the "sudo service cron stop" again. If it works the same way it did for me then this time, when you stop it, it wont give you the error message. Then reboot one more time and, again if it works like it did for me, cron should be running.

---

### Post by monomox3000 on 2010-07-31
Jim, I did exactly what you posted but didn't work for me. 
I see that the bug report in launchpad didn't get many people's attention.

---

### Post by sixmoney on 2010-08-25
In my case, I'm able to add jobs to crontab but all jobs added to /etc/cron.daily, cron.hourly are not run. Hope this can help.

This can be a work-around.

---

### Post by monomox3000 on 2010-08-27
I solved my problem about two weeks ago by doing a fresh install of LL.
[B][SIZE=5][SOLVED]
;)
[/SIZE][/B]

---

