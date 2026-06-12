---
title: "Poweroff at certain times at certain weekdays."
date: 2006-05-19
forum: General Help
---

### Post by daller on 2006-05-19
Hi There,

I'm building up a showroom-pc from scratch...

It's basic functions is to control 36 lighteffects and 32 highspeakers (16+16)

Thanks to Janos, it was pretty easy to get the hardware working:

Hardware, See: [http://elav.dk/eshop/index.asp?PRO_ID=95481](http://elav.dk/eshop/index.asp?PRO_ID=95481)

Software, See: [http://sourceforge.net/projects/sispm](http://sourceforge.net/projects/sispm)

Furthermore, I would like it to shutdown (It turns on every day at 10:00) at the following times:

Monday-Friday: 19:00
Saturday: 14:00
Sunday: 10:10 (basically, just after it has started up - We're closed on sundays!)

Anyone wanna write me a script, or help me do it?

---

### Post by Randomskk on 2006-05-19
As far as making the script goes..
If you use the command "init 0" in a script, it should shut the system down (script will need to be run as root though).
You can get the day and time using:
date +%w\ %R

So you should be able to make a script that will constantly check the time and day, and if it matches any of your shutdown times, will shut down the computer.

---

### Post by ob211 on 2006-05-20
You might be able to do this with a cron job (using something like KCron or the command line), but im not sure how to do it.

---

### Post by daller on 2006-05-20
Kcron seems like a nice solution! - Thanks!

But running "init 0" needs superuser privs!

What command does the "Shut-down"-option for normal users use? (K -> Log off -> Shut down the computer)

And giving general permission to run "init 0" without password seems like a security-issue.

---

### Post by Rog131 on 2006-05-20
In konsole:

kdesu kcron

click day and time (it's graphical).
To program line: /sbin/shutdown -h now

man shutdown tells that: 
> shutdown  brings  the system down in a secure way.  All logged-in users are notified that the system is going down, and login(1) is blocked.  It is  possible  to shut the system down immediately or after a specified delay.

---

### Post by daller on 2006-05-20
As it is now, I can't run sudo or kdesu...

I messed with my /etc/sudoers, and now I can't do anything!

What's the root password? (if I go to tty1 and login as root)

---

### Post by daller on 2006-05-20
Hey, booting in recovery mode, does start as the root-user right?

I never understood that! (before now :)) - It seems like a serious security-issue... But of course, anyone who gains direct access to the computer can access the data in some way...

---

### Post by daller on 2006-07-11
Is there a passwordless command to shutdown a pc?

This only works with the sudo-password:

 /sbin/shutdown -h now

And I'm not editing /etc/sudoers if it's possible without!

---

### Post by ob211 on 2006-07-11
It might be best to ad a line like this to sudoers, it should let you use 'sudo shutdown' without a password, while still making you use a password for other programs.
```

<username>	ALL = NOPASSWD: /sbin/shutdown

```

---

