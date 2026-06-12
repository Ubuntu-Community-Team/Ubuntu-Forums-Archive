---
title: "Cron doesn't work"
date: 2006-06-06
forum: General Help
---

### Post by Lyle on 2006-06-06
Hello,
I have a Problem with cron. It is installed, it is running (at least I think so), the crontab file is there. All is fine, except that nothing happens. I use the following crontab file for testing purposes:

*/1 * * * * echo "crontab test"

but there is no output. It's the same, when I'm using sudo. 

Has anyone an idea how to solve this problem

---

### Post by xtacocorex on 2006-06-06
You need to allow cron jobs to users with the following files:
/etc/cron.allow
/etc/cron.deny

In cron.allow you list users that have access to cron, you and root, and any other user you want to have cron jobs.

You don't need a cron.deny unless you want to deny people cron jobs and isn't needed as Ubuntu sets up a default deny to cron unless you are listed in a cron.allow file.

Hope that doesn't confuse you.

---

### Post by ifokkema on 2006-06-06
[QUOTE=Lyle]Hello,
I have a Problem with cron. It is installed, it is running (at least I think so), the crontab file is there. All is fine, except that nothing happens. I use the following crontab file for testing purposes:

*/1 * * * * echo "crontab test"

but there is no output. It's the same, when I'm using sudo. 

Has anyone an idea how to solve this problem[/QUOTE]

Not sure if it's related, but you could just try:
```
* * * * * echo "crontab test"
```

The /1 doesn't do much in this case.

---

### Post by cyracks on 2006-06-06
From cronttab:
# m h dom mon dow **user**  command
Try this
```
 * * * * *  root mkdir /tmp/test
```

---

### Post by xtacocorex on 2006-06-06
[QUOTE=cyracks]From cronttab:
# m h dom mon dow **user**  command
[/QUOTE]

If you're doing system crons, you don't need the user.

As an example, here is a cron that I run at every reboot and this works since the cron jobs run after everything is mounted.
```
@reboot /home/bobw/bin/scaleset
```

All it does is run the bash script and that script changes the permissions to /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor and /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq so that I can change their values on the fly as non-root.

---

### Post by thasheep on 2006-06-06
Crons don't output to a terminal unless you explicitly tell them to. eg the following will show up on tty6 (<ctrl><alt>f6)```
6 6 6 * * root echo omen > /dev/tty6
```so the OP wouldn't be able to see whether the cron was run or not.
A system cron can be added to /etc/crontab. The above line is valid as a system cron.
If it's a user cron, add your username to /etc/cron.allow (create if it doesn't already exist) and then 'cron -e' as that user to create the cron. Leave out the user field (user cron is run as that user), eg
```
1 * * * * mkdir /tmp/omen
```

---

### Post by ifokkema on 2006-06-06
[QUOTE=thasheep]Crons don't output to a terminal unless you explicitly tell them to.[/QUOTE]

If you create your crons using crontab -e, the output will be mailed to you by default. But you're right - he didn't specify how the cron was set.

---

### Post by Lyle on 2006-06-06
Well, this
> 
You need to allow cron jobs to users with the following files:
/etc/cron.allow
/etc/cron.deny

solved the problem, and that 
> Crons don't output to a terminal unless you explicitly tell them to. eg the following will show up on tty6 (<ctrl><alt>f6)
was the reason I didn't noticed it at first. 

I thank all of you for your help

By the way: Four minutes elapsed between the question and the solution. I would say that's pretty good for a community.

---

### Post by xtacocorex on 2006-06-06
Glad that I could help.

@thasheep:
I didn't know that, so thanks for that bit of useful information.

---

### Post by KillerKiwi on 2006-06-06
check out gnome-schedule

---

### Post by cyracks on 2006-06-06
[quote=xtacocorex]
 I've just switched from KDE to Gnome, I need time to adjust
[/quote] Could you tell me why did you switch ? Just curiosity or something else ?

---

### Post by xtacocorex on 2006-06-06
[QUOTE=cyracks]Could you tell me why did you switch ? Just curiosity or something else ?[/QUOTE]

I left you a PM because it's sort of long, hope that's ok.

---

