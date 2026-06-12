---
title: "Upstart sysvinit integration"
date: 2010-06-17
forum: General Help
---

### Post by gravitz on 2010-06-17
Hi,

I use ubuntu lucid server and have a sysvinit start up script thats been working for me for years. I only started using lucid recently, and found out about upstart when my script stopped working. The script depends on mysql server, which unlike in older versions, now uses upstart. Migrating my script to upstart isn't an alternative for now.

I would like to continue using my sysvinit, but how do I make sure it starts after mysql?

Rgds,

Eli

---

### Post by john newbuntu on 2010-06-17
Move the /etc/init/mysql.conf to say, /etc/init/mysqld.conf.disabled.  This will prevent upstart from running mysql.

I am assuming you are familiar with creating a sysV style init job.  Create your start and kill scripts using any of the following methods(and perhaps more) to set up mysql as well as your script.  Obviously, make sure that mysql start script has a lower sequence number than your script but a higher one than networking.  I'd suggest creating it at runlevels 2 through 5.
1. update-rc.d,
2. sysv-rc-conf
3. just by putting it in /etc/init.d and creating symlinks appropriately to the /etc/rc*.d/

If you want to do it the upstart way, you would create a file like /etc/init/postmysql.conf and start it after a known event is emitted by the /etc/init/mysqld.conf script.

---

### Post by gravitz on 2010-06-17
Hi,

Thanks for the help. I'd rather mysql remain upstart, and I convert my postmysql script. But what I was hoping for was an easier means to make sure my script starts after upstart has finished starting up mysql, without converting my script to upstart. I am guessing combining the 2 (upstart and sysvinit) that way can't be done.

Thanks

---

### Post by john newbuntu on 2010-06-17
upstart and sysV init run asynchronously.  So you have no way of knowing when to kick things off.  Some suggest using a sleep command in an rc script and run it after a few seconds.  But that involves a race condition, which is why it is good to go the "all upstart" way or "all sysV init".

You could also try writing an rc script in an infinite loop polling for a file/process of some sort to have come up and then kicking your command off.

---

### Post by gravitz on 2010-06-17
I will try and do that (the second option).

One thing I thought of, is write an upstart script that execs the original rc. Would that work?

---

### Post by john newbuntu on 2010-06-17
As long as it runs after the mysql daemon starts up, that should work.  You could also try exploring the post-start stanza of upstart.

---

