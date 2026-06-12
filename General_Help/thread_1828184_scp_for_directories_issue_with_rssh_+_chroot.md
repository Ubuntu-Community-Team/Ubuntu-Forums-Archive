---
title: "scp for directories issue with rssh + chroot"
date: 2011-08-18
forum: General Help
---

### Post by luvshines on 2011-08-18
I have setup an SCP and SFTP server using rssh.

The rssh.conf file reads:
```
allows scp
allows sftp
chroot=/var/opt/scproot
```

And my user's homedir point to:
/var/opt/scproot/scpshares

My /var/opt/scproot contains all the lib64, etc, bin, var  and other directories required for rss + chroot setup

I create SCP shares in seperate filesystem and them mount bind them in individual directories in scpshares

I have set following permissions
```
755 to /var, /var/opt
751 to /var/opt/scproot
755 to lib64, etc, bin, var ... under /var/opt/scproot
755 to /var/opt/scproot/scpshares
```

Logging in from sftp brings me directly to scpshare folder where I am able to see all the available shares.
Doing 'cd ..' there and then trying to list, give permission error because of 751 permission I suppose

However, when I do
```
scp -r myuser@scpserver: .
```

I don't know why it starts copying files from /var/opt/scproot and I am able to download lib64, etc directories.
It treats the chroot directory as the root folder for the user, I guess

Why is scp showing this behaviour and how to restrict it to /var/opt/scproot/scpshares only ?

---

### Post by luvshines on 2011-08-19
**[COLOR="Red"]*** bump ***[/COLOR]**

---

