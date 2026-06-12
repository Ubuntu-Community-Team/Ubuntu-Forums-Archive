---
title: "Need help with crontab under root"
date: 2010-03-17
forum: General Help
---

### Post by Rob@ThePCWiz.info on 2010-03-17
Hi, I'm trying to get mySQL Daemon to start when the machine starts up (and it requires root privileges to run).
The command to startup would be
```
sudo /etc/init.d/mysql start
```
however that would prompt for a password, and that would not be very well possible now would it?
Now, if i try to start it up without being root, it will not start.
So this is my problem, maybe someone out there would know a bit more about this than me.

---

### Post by prodigy_ on 2010-03-17
IIRC, ```
mysql --user=<your_username> --password=<your_password>
``` should work. This way, however, your password will be visible in ps output (unless it's been changed).

---

### Post by mikewhatever on 2010-03-17
You could try and add '/etc/init.d/mysql start' to /etc/rc.local. No need for 'sudo' there.

---

### Post by Rob@ThePCWiz.info on 2010-03-17
> **mikewhatever said:**
> You could try and add '/etc/init.d/mysql start' to /etc/rc.local. No need for 'sudo' there.

So lets say, that i made a symbolic link in /etc/rc.local to /etc/init.d/mysql
(or better yet) lets say i made a symbolic link to it in /usr/bin, i could just (in the last case) i could type "mysql start" and it would not require sudo?

**EDIT**
I just had a concern, about the fact that I have users that I provide shell accounts for, and I don't want them to be able to manipulate the mysql daemon, so please, it's actually pretty dire that it remains a command that requires root.

---

### Post by mikewhatever on 2010-03-17
> **Rob@ThePCWiz.info said:**
> So lets say, that i made a symbolic link in /etc/rc.local to /etc/init.d/mysql
(or better yet) lets say i made a symbolic link to it in /usr/bin, i could just (in the last case) i could type "mysql start" and it would not require sudo?

**EDIT**
I just had a concern, about the fact that I have users that I provide shell accounts for, and I don't want them to be able to manipulate the mysql daemon, so please, it's actually pretty dire that it remains a command that requires root.

A symlink in /usr/bin would not be executed on startup, and if you type "mysql start", it will ask for password. If you want a symlink, make one in /etc/rcS.d. Take a look at /etc/rcS.d/README.

Edit: In fact, there may be some symlinks already in rcX.d, according to this thread [http://ubuntuforums.org/showthread.php?t=1079341](http://ubuntuforums.org/showthread.php?t=1079341).
Try <ls /etc/rc* | grep -i mysql>.

---

### Post by squareff255 on 2010-03-17
> **Rob@ThePCWiz.info said:**
> Hi, I'm trying to get mySQL Daemon to start when the machine starts up (and it requires root privileges to run).
The command to startup would be
```
sudo /etc/init.d/mysql start
```
**however that would prompt for a password, and that would not be very well possible now would it?**
Now, if i try to start it up without being root, it will not start.
So this is my problem, maybe someone out there would know a bit more about this than me.

Well, actually, you COULD use your password if you wanted. You could use this command:
```

echo "putyourpasswordhere" | sudo /etc/init.d/mysql start

```
but then if someone had access to that code, they would see your password...

---

