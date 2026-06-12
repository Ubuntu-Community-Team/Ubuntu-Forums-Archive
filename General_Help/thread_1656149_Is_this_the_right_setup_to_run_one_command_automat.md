---
title: "Is this the right setup to run one command automatically at startup?"
date: 2010-12-30
forum: General Help
---

### Post by Rytron on 2010-12-30
Hi guys.

I want to auto run ```
sudo updatedb
``` at Ubuntu startup. Is this okay: [http://i.imgur.com/FrMFp.gif](http://i.imgur.com/FrMFp.gif)

---

### Post by matt_symes on 2010-12-30
Hi

I would run it as a cron job with the @reboot flag under roots crontab

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

That way you will not need sudo.

What you are trying to do will not work.

Kind regards

---

### Post by James78 on 2010-12-30
It's fine except for one problem. Sudo needs a password to run the command. So either you need to make sure the command is being run as root (in which case you won't need to sudo it), or you need to explicitly allow your user to use sudo without a password. If you'd like however, you could just allow sudo to execute without a password for that command only.

```
# your user can use sudo for all commands, no password, not recommended
<username> ALL=NOPASSWD: All
# your user can use sudo without a pass for updatedb only
<username> ALL=NOPASSWD: /usr/bin/updatedb
```

Of course, as the person above me stated however, there are different ways about going through this. Like I said, it's probably just best to have it run as root. As mentioned above, Cron is one way to do it.

---

### Post by Rytron on 2010-12-30
Thanks guys for clearing that up. I may give 'Scheduled tasks' from Ubuntu Software Center a try.

Update: Would this be okay? Or should I change the Default Behaviour dropdown box?

---

### Post by dcstar on 2010-12-31
> **Rytron said:**
> Hi guys.

I want to auto run ```
sudo updatedb
``` at Ubuntu startup.

Pointless:

```
       updatedb  is  usually  run daily by cron(8) to update the default data&#8208;
       base.

```

---

### Post by matt_symes on 2010-12-31
Hi

> **dcstar said:**
> Pointless:

```
       updatedb  is  usually  run daily by cron(8) to update the default data&#8208;
       base.

```

Yes. It's actually run as part of cron.daily 

From cron.daily: 

```
matthew@matthew-laptop:/etc/cron.daily$ ls
0anacron  aptitude      dpkg       mlocate             sysstat
apport    bsdmainutils  logrotate  popularity-contest
apt       chkrootkit    man-db     standard
matthew@matthew-laptop:/etc/cron.daily$
``` 

mlocate is a script. <snip> from mlocate script...

```
[ -x /usr/bin/updatedb.mlocate ] || exit 0
```

runs updatedb.mlocate to update the db.

Following updatedb command

```
matthew@matthew-laptop:/etc/cron.daily$ which updatedb
/usr/bin/updatedb
matthew@matthew-laptop:/etc/cron.daily$ ls -l /usr/bin/updatedb
lrwxrwxrwx 1 root root 26 2010-10-14 21:32 /usr/bin/updatedb -> /etc/alternatives/updatedb
matthew@matthew-laptop:/etc/cron.daily$ ls -l /etc/alternatives/updatedb 
lrwxrwxrwx 1 root root 25 2010-10-14 21:31 /etc/alternatives/updatedb -> /usr/bin/updatedb.mlocate
matthew@matthew-laptop:/etc/cron.daily$
```

After following symlinks also runs updatedb.mlocate.

Moral of the story, read the manual first ;)

Cheers DC star.

Kind regards

---

