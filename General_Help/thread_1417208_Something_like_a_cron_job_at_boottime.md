---
title: "Something like a cron job at boottime"
date: 2010-02-27
forum: General Help
---

### Post by stardustdk on 2010-02-27
Hey all.

Is it possible to make something a la a cron job at boot time?

Like an autoupgrade of the software.

Shall work in Ubuntu 9.04+

Best regards

Stardustdk

---

### Post by dcstar on 2010-02-27
> **stardustdk said:**
> Hey all.

Is it possible to make something a la a cron job at boot time?

Like an autoupgrade of the software.

Shall work in Ubuntu 9.04+


Software "autoupgrade" is already run a few minutes after bootup as part of the Update Manager settings.

All daily (and other) cron jobs are already automatically run after bootup by the anacron system.

---

### Post by jswoods7 on 2010-02-27
If you mean run a command at start up, take a look at the /etc/rc.local file.

---

### Post by amrypma on 2010-02-27
you can also make a line in a crontab starting with @reboot instead of the usual time notation.

```
@reboot SHELL=/bin/bash ; sleep 30 ; screen -d -m -c $HOME/.screenrc-auto
```

I use this line to start screen at a reboot.To read up look at the manpage for crontab section 5

```
man 5 crontab
```

---

### Post by stardustdk on 2010-02-27
Thanks, I mean command at startup yes...

Best regards

Stardustdk

---

### Post by amrypma on 2010-03-03
and did you get it to work?

---

### Post by stardustdk on 2010-03-03
think i did...

Put
> 
apt-get update -y
apt-get dist-upgrade -y
apt-get autoclean

in /etc/rc.local and 

> #!/bin/bash
apt-get update -y
apt-get dist-upgrade -y
apt-get autoclean

i a file, i named "cronupdate", that i put in /etc/cron.hourly and maked executable.

Best regards

---

### Post by amrypma on 2010-03-10
Ubuntu isn't so unstable that you need to update your system every hour. Even once a day seems very often to me. About once a week will do fine.

Also, I like to know what gets installed en when it's installed. So why not put some sudo's in there so you only have to type update (i.e. put it in /usr/local/bin or $HOME/bin). Sure you need to type your password once more but at least you know whats going on.

And lastly, have a look at the deborphan and debfoster packages.

---

### Post by dcstar on 2010-03-10
> **stardustdk said:**
> 
........
i a file, i named "cronupdate", that i put in /etc/cron.hourly and maked executable.


Considering that most repositories rarely have all the packages fully downloaded by the time they advertise updates, this sort of thing is almost guaranteed to wreck a system.

Total insanity.

---

### Post by stardustdk on 2010-03-10
I have found that out too.

well changed it to this:

> #!/bin/bash
aptitude update -y
aptitude safe-upgrade -y
dpkg --configure -a
aptitude autoclean

The safe-upgrade prevents the system failure.

The *dpkg --configure -a*, well: To often i find that the downloaded files dosn't configure right :(.

Best regards

---

