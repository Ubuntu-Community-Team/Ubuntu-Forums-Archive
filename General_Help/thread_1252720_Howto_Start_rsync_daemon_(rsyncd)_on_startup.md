---
title: "Howto: Start rsync daemon (rsyncd) on startup"
date: 2009-08-29
forum: General Help
---

### Post by dawbomb on 2009-08-29
Many people might find the need to have rsync run as a daemon on system startup (for example, my server connects to computers on the network to backup using rsync), and unfortunately the rsync manual page isn't very descriptive in this regard, which is strange seeing as this is so easy to do.

All code in the following howto is entered into a terminal.

This howto works in Ubuntu 9.04 (both 32 and 64 bit versions), and should work exactly the same in all other Ubuntu editions (and most other Linux distro's)

[LIST=1]
[*]Check that rsync is installed:
```
sudo apt-get install rsync
```

[*]Create an rsyncd config file:
```
sudo nano /etc/rsyncd.conf
```

Here is a sample config file (this assumes rsync is being used to backup the documents directory from an external pc).  The syntax is similar to that of samba:
```
#motd file = /etc/rsyncd.motd
log file = /var/log/rsyncd.log
pid file = /var/run/rsyncd.pid
lock file = /var/run/rsync.lock

[documents]
   path = /home/user/Documents
   comment = User's Documents folder
   uid = user
   gid = user
   read only = no
   list = yes
   hosts allow = 10.0.0.1/0
   auth users = backup
   secrets file = /etc/rsyncd.scrt
   strict modes = false
```

Type the following into a terminal to see more info on the rsyncd.conf file:
```
man rsyncd.conf
```

[*]Create a password file for the backup user:
```
sudo nano /etc/rsyncd.scrt
```

Put in all users and passwords in plaintext:
```
backup:PassWord
user2:pAssWord2
```

Type the following into a terminal to see more info on the rsyncd.conf file:
```
man rsyncd.conf
```

[*]To start rsyncd upon system startup edit the file /etc/defaut/rsync:
```
sudo nano /etc/default/rsync
```

Simply change the line
```
RSYNC_ENABLE=false
```
to
```
RSYNC_ENABLE=true
```

[*]Reboot your computer

[*]To check that rsync is running, open the logfile:

```
sudo nano /var/log/rsyncd.log
```

If there is a line which says something like "rsyncd version 3.0.5 starting, listening on port 873" right at the end of the file, its happy days and rsync now runs on startup!
[/LIST]

---

### Post by YuiDaoren on 2010-11-08
Thank you for this howto. :)

---

