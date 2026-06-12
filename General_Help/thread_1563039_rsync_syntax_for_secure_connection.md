---
title: "rsync syntax for secure connection"
date: 2010-08-28
forum: General Help
---

### Post by errorken on 2010-08-28
I'm confused. According to the rsync docs ([http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html)), one should use '::' in the rsync syntax when connecting to an unsecure rsync daemon.
One should use ':' when connecting via ssh. In the latter case the daemon should not be running (it is started automagically or something for that ssh connection, no idea how this works, but apparantly it does)

So, in my setup, I have no rsync daemon running.

This command : user@user:~$ rsync user@192.168.2.50::share/*
Returns this:
rsync: failed to connect to 192.168.2.50: Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(122) [Receiver=3.0.7]

Good-> since this is an unsecure connection (::) and no rsync daemon is running

This command: user@user-laptop:~$ rsync user@192.168.2.50:share/*
Gives me a directory listing:
user@192.168.2.50's password: 
-rwxr--r--   341328896 2010/07/19 ...
...
..

Good-> since this is a secure connection (:) and rsync is automagically booted over ssh.

But then it gets weird.
If you start to use the '-e ssh' option, with a single ':' in the url nothing changes, and you still get a directory listing.
But, if you use a double '::' in combination with the '-e ssh' option:

user@user-laptop:~$ rsync -e ssh user@192.168.2.50::share/*
user@192.168.2.50's password: 
Password: 
@ERROR: chroot failed
rsync error: error starting client-server protocol (code 5) at main.c(1524) [Receiver=3.0.7]
user@user-laptop:~$ 

The password is suddenly asked twice (its my guess its one time for ssh and one time for rsync) but now I get an error about 'user' not being allowed to chroot?

So, my questions are:

1. Why does using a normal non root user, '-e ssh' , and '::' give a chroot exception, why a normal non root user and ':' does not? Apparantly both run over SSH, since there is no daemon running, and there is no connection error.

2. What is the '-e ssh' for if you normally use the ':' and '::' to toggle between secure and non secure?

I'm asking this question because I have a NAS which I use the schedule rsync backups. Apparantly, the NAS uses the '-e ssh' option AND the '::'. I have no control over this, so its  results in a connection failure because of the chroot.
When I run it as root user, it works ok.

---

