---
title: "problem with cron timing"
date: 2010-01-31
forum: General Help
---

### Post by nima_a on 2010-01-31
Hi, 
1. I've changed the crontab file (/etc/crontab) inorder to force cron.daily to execute at the specific time, as follows  :
```
30 0    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```which I expected to execute @ 00:30 every day,

2. after that, I've modified /etc/cron.daily/sysklogd as follows inorder to append date in the result log file ("-d -D %Y%m%d" has been added to savelog command )
```
savelog -d -D %Y%m%d -g adm -m 640 -u ${USER} -c 7 $LOG >/dev/null
```3. finally /etc/syslog.conf has been modified to rotate auth.log day by day , as follows : (*.* has been added to the first of the line)
```
*.*;auth,authpriv.*                     /var/log/auth.log

```so, after restarting cron,sysklogd, .. deamons, I expected that the "auth.log.DATE" files to create every day @ 00:30
but it (rotation of the auth.log file) happens 07 or 08 AM :
```
nima@nima-desktop:~$ ls -lh /var/log/ | grep auth.log --color
-rw-r----- 1 syslog   adm      1.2M 2010-01-31 10:02 auth.log
-rw-r----- 1 syslog   adm      858K 2010-01-30 08:57 auth.log.20100130
-rw-r----- 1 syslog   adm       11M 2010-01-31 07:47 auth.log.20100131
```and the question is : **why ?**

thanx in advance :)

---

### Post by john newbuntu on 2010-01-31
Did you have your computer turned on all night long for cron to run?  If it were turned off before 00:30 hrs, then the next time you turn it on, anacron takes over and runs those daily or other jobs (Look at /etc/anacrontab for details)

---

### Post by nima_a on 2010-01-31
> **john newbuntu said:**
> Did you have your computer turned on all night long for cron to run?  If it were turned off before 00:30 hrs, then the next time you turn it on, anacron takes over and runs those daily or other jobs (Look at /etc/anacrontab for details)
yes sir, it has been turn on :)
and thanx for your reply :)

---

### Post by john newbuntu on 2010-01-31
If the first part of the statement:
test -x /usr/sbin/anacron
is true, would it ever run the second part?
So, if /usr/bin/anacron is executable by root, forget the second part being run.  You will have to remove the test condition.

---

### Post by nima_a on 2010-01-31
Dear sir, the line above is the default template to run cron.daily scripts on all ubuntu machines; I just modified the execution time; also, the scripts executes correctly, but **not in the proper time**

---

### Post by john newbuntu on 2010-01-31
That's right.  All I am suggesting is to remove the test condition. i.e., change your /etc/crontab entry to the following and see if it helps:

```
30 0 * * *    root    cd / && run-parts --report /etc/cron.daily
```

---

### Post by nima_a on 2010-02-01
It seems strange !
I tried to execute the cron.daily task manually with the following command :
```
 $ bash /etc/cron.daily/sysklogd
```and It worked exactly how I expected (so there's no problem with rotating)
then I thought , may be the problem is with the cron.daily execution time, so I enabled cron.log and I noticed that cron.daily executes exactly in the correct time ! (with the help of cron's log file), but nothing executes in action (on that time) !
so , I checked the crontab's command again , because the only option for this failure should be in the cron's executed command :
```
 root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ) 
```So, with having a closer look to the the structure of the crontab line, ...
1. what is the need of checking anacron to be executable ?!? which is true at the moment while I was testing , and so it was obvious that nothing will execute in action ... damn !
2. I tried to manually execute the second part of the command :  ( which is : cd / && run-parts --report /etc/cron.daily - ofcourse with the root user), and nothing happened again, ! why ? in this case , I just see a line appending to my cron.log file, as follows :
```
 Feb  1 23:12:40 nima-desktop anacron[16183]: Updated timestamp for job `cron.daily' to 2010-02-01 
```

---

### Post by nima_a on 2010-02-02
any opinions ?

---

### Post by rnerwein on 2010-02-02
hi
my opinion is: read the ******* manual: man cron, man crontab ...
ciao :-)

---

### Post by nima_a on 2010-02-02
> **rnerwein said:**
> hi
my opinion is: read the ******* manual: man cron, man crontab ...
ciao :-)
Oh yeah ?!?!?
would you please tell us in which part of the *** manual, mentioned anything about this issue ?

---

### Post by rnerwein on 2010-02-02
hi
first i have to admit that first i was confused too when i saw this post.
but: first look at cron. cron is running crontab and all stuff in cron.d. here cron will find anacron and anacron will run /etc/anacrontab and if anacron isn't x then run-parts will run all the files find in cron.??*
i think i understand now what's going on
ciao

---

### Post by john newbuntu on 2010-02-02
1. As I understand it, anacron takes precedence over cron, which is probably why the executable bit is checked.
2. Are you sure the command did not execute? I would suggest throwing in a simple shell script into /etc/cron.daily that echo's date to a file and exits with a 0 return status.  Now try run your run-parts command and check its execution.  syslogs will not display the specific script/job name.  You can also check if your script is run using:
```
sudo run-parts --verbose /etc/cron.daily
```

---

### Post by nima_a on 2010-02-03
@[john newbuntu]("http://ubuntuforums.org/member.php?u=956991") & @[rnerwein]("http://ubuntuforums.org/member.php?u=972890"): first, I should appreciate your time to read this topic ...
Well , well ,well, ...
1. first I tried to write a fake script and put it on cron.daily inorder to see what is happening, and nothing happened,
2. then I tried to remove "test -x /usr/sbin/anacron" from crontab's line, and check to see if the fake script executes or not, and in this case, if the fake script's name come before apt & aptitude scripts , such as 0script, the script will execute normally, but if the name comes after apt & aptitude (which seems to take a long time to execute), the script runs with delay ...
I've test it on another machine (ubuntu 8.04 hardy - desktop) and the same thing occured ...(both machines have ubuntu 8.04 LTS)
seems strange ...

so I think I have to find an answer for the following questions :
**1.** the "test -x /usr/sbin/anacron" issue ? what is the need of this command to be there !?! as far as I know, anacron searches for missed cron jobs, and execute them; I don't undrestand why anacron have to be checked when the aim is to execute cron.daily jobs normally !?! and as I mentioned above, nothing executes when this command executes before cron.daily execution with run-part
**2.** why apt & aptitude takes a long time to execute
**3.** why these scripts are executing sequentially (I think it's not ok for a critical cron.daily script to wait for another one to complete)
**4.** is there any way to apply priority in executing cron.daily scripts (except changing their names !)

P.S : the command : sudo run-parts --verbose /etc/cron.daily , also shows that there's /etc/cron.daily/apt take a lot of time to execute

---

### Post by chitresh4u on 2010-02-03
due to the test parameter, anacron is taking over cron and is rescheduling the jobs depending on the last time-stamp of execution. 

Check following thread: 

[http://ubuntuforums.org/showthread.php?t=375044](http://ubuntuforums.org/showthread.php?t=375044)

---

### Post by nima_a on 2010-02-03
> **chitresh4u said:**
> due to the test parameter, anacron is taking over cron and is rescheduling the jobs depending on the last time-stamp of execution.

Check following thread:

[http://ubuntuforums.org/showthread.php?t=375044](http://ubuntuforums.org/showthread.php?t=375044)



Hi chitresh4u and thanx four your link,
let's have a quote from your link :
> 
The test for /usr/bin/anacron ensures that cron runs the daily, weekly and monthly script only if anacron is not installed. Take a look at the file /etc/anacrontab. It is also configured to run the daily, weekly, and monthly scripts. (Well, on my system it is; I am running Ubuntu 6.06.). So, cron is set up to run the hourly script, and anacron is set up to run the daily, weekly and monthly scripts.

This begs the question: If anacron normally takes care of the daily, weekly and monthly scripts, why did the developers also put entries in crontab for these scripts that only run if /usr/sbin/anacron does not exist? Why would anacron not exist? (OK, if you removed the anacron package, this provides a 'failsafe' that ensures that the scripts still run, but why would you remove anacron?)
So, inorder to find an answer for question #1, ...
It seems that anacron will take the responsibility of executing cron.daily jobs; so let's take a closer look to the following line :
```
  00 11   * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ) 
```it means that if the anacron package has been installed & if it's executable, do not ever execute /etc/cron.daily with the help of cron !!!
ok, so anacron will execute the cron.daily jobs, ... let's take another look to the anacron's configuration file which executes cron.daily scripts :
```
 1       5       cron.daily      run-parts --report /etc/cron.daily 
```note 1 : I've remove nice command (u know why ...)

but, what about the timing ? all we know is that the perdiod (the first item which is 1 ; defines the number of days has to pass between executions of command), and delay (which is 5; says that the script should be executed 5 minutes after calling) ... and all the references to the latest call will save of /var/spool/anacron/cron.daily (in our context) - that's all

so, I think we can conclude that the time mentioned in cron.daily (in my example : 11:00 ) is completely useless, because the term ** test -x anacron ** do not actually run anacron (just test it to be executable); besides , only date will save on /var/spool/anacron (and not time);

so inorder to test it, I made changes on /var/spool/anacron/cron.daily manually be changing it's date (which was the current date) to yesterday, and restart(actually stop/start) the /etc/init.d/anacron and I saw that the cron.daily scripts began to run after 5(anacrontab's dalay time) minutes and completely regardless of the /etc/crontab 's cron.daily time !!! what is this ? **so in this case,  I think we can conclude that crontab 's time for cron.daily scripts is completely useless, and another question rising which is : how anacron handles execution time** (time, not date which is stored on /var/spool/anacron/cron.daily)?


!

and about Q #2, I checked the /etc/cron.daily/apt script and found the following line :
```

# sleep random amount of time
random_sleep

```which takes 682 secs in a sample test of mine; I think this may cause problems when these scripts are running sequentially and we have important scripts which come after apt ....

---

### Post by john newbuntu on 2010-02-03
nima_a,

**1.** the "test -x /usr/sbin/anacron" issue ? what is the need of this command to be there...
A: How many of us keep our PCs/laptops running 24X7? The answer is some or most, which means that the rest need a way to get the maintenance jobs to run(cron.daily etc).  Hence the need for anacron.  The check for executable bit on anacron is to check if it exists.  If so, anacron runs the routine jobs for us, irrespective of whether your computer is always on or not. Oh and BTW cron is a daemon but anacron is not it needs to be triggered, which is done either by the upstart (when you turn on the system) or by cron(when you never power off your comp).  You can not schedule jobs with anacron.

**2.** why apt & aptitude takes a long time to execute?
A: Apt takes a long time to execute because of a random sleep that has been introduced into the apt script so as to not hammer the apt server mirrors.  If we all have the same crontabs/anacrontabs and if the update runs at the same time, just imagine the load on the software server.  aptitude, I am guessing from the script involves compares and compression of a file that might take some time. I have not checked this though.
[B]
3.[/B] why these scripts are executing sequentially (I think it's not ok for a critical cron.daily script to wait for another one to complete)
A: Someone else who was involved with the design can answer this better.  But, run-parts by default runs one task at a time in lexical order as you might have seen.  This makes it easy to just execute all jobs in a directory and not care on dependencies.  I did a man on run-parts and found an option called --new-session that might help you run several jobs.
If you really need a job to run at a certain time, you must make it a separate job on the crontab file.

**4.** is there any way to apply priority in executing cron.daily scripts (except changing their names !)?
A: Not that I am aware of.  But there are several workarounds, for example, call a wrapper script that in turn calls your jobs in a specific order.  You could take is one level up and just && your commands on the crontab.

---

### Post by john newbuntu on 2010-02-03
nima_a, for your post #15, 
As you may have gleaned from man anacron, anacron is only date and delay based not time based.  So the time part is not used.
Yes crontab's time is not used (in cases where there is a test for -x anacrontab).  Instead, anacron's date and delay gets used since anacron is invoked by cron (via /etc/cron.d)

Most of what I have been writing here in answering you is from a Karmic perspective (no pun intended).  The behavior might be different in other flavours.

---

### Post by nima_a on 2010-02-03
Hi john, ...
> anacron is only date and delay based not time based.  So the time part is not used
> Yes crontab's time is not used (in cases where there is a test for -x anacrontab)

so, we can conclude that :
1. crontab 's time is useless, when there's "test -x /usr/sbin/anacron" and anacron is execuable (in most cases)
2. there's no way to tell anacron to run @ the specific time ?

---

### Post by nima_a on 2010-02-03
and as the final note, here's a quote from anacron's homepage (sourceforge) :
> 
 Anacron is not an attempt to make cron redundant.  It cannot be used to schedule commands at intervals smaller than days. **It also does not guarantee that the commands will be executed at any specific day or hour. **
  **It isn't a full-time daemon**.  It has to be executed from boot scripts, from cron-jobs, or explicitly. 

special thanx to [john newbuntu]("http://ubuntuforums.org/member.php?u=956991") , [chitresh4u]("http://ubuntuforums.org/member.php?u=636700") & [rnerwein]("http://ubuntuforums.org/member.php?u=972890") for participating in this topic :)
P.S : just noticed that anacron is not installed in server editions by default :)

---

### Post by chitresh4u on 2010-02-03
As far as I understand, desktop/laptop computers are not generally supposed to be running 24x7. Hence anacron is included to ensure that your daily/montly scripts are run almost perodically irrespective of the computer's up time. If you really want to stick to cron and your precise timing then you can remove tests from crontab or enter your desired commands in new line.

On the other hand servers are supposed to be running 24x7 so they may not be installing anacron by default.

And Yeah, I completely agree that, the information about the 'default' over-riding by anacron should be written somewhere in comments in crontab. Apparently it became clear when googled about anacron. I was also annoyed to find random running time of cron.daily scripts.

PS: I suppose you can mark this thread solved.

---

### Post by chitresh4u on 2010-02-06
[http://flukylogs.blogspot.com/2010/02/cron-scripts-executing-at-wrong-time.html]("http://flukylogs.blogspot.com/2010/02/cron-scripts-executing-at-wrong-time.html")

---

