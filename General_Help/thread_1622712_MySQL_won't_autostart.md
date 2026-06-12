---
title: "MySQL won't autostart"
date: 2010-11-15
forum: General Help
---

### Post by ToadJamb on 2010-11-15
I installed MySQL from binaries and through some work, googling, and experimentation have gotten it to work.  With one little problem.  It won't start automatically on system start (and presumably would be beaten into submission on shutdown instead of complying nicely).  I have read about upstart and jobs and update-rc and runlevels and etc/init.d and how upstart is the future blah blah blah, but nothing that gives me enough to actually figure out what I need to do.  So I appeal to you, the kind folks of ubuntuforums, to assist me if you are able and willing.

I have tried several other ways, but this is what I currently have:

1. I copied /usr/local/mysql/support-files/mysql.server to /etc/init.d per the following instructions in said mysql.server file:

```
# Usually this is put in /etc/init.d (at least on machines SYSV R4 based
# systems) and linked to /etc/rc3.d/S99mysql and /etc/rc0.d/K01mysql.
# When this is done the mysql server will be started when the machine is
# started and shut down when the systems goes down.
```
2. Again following these instructions, I created the indicated symlinks in the rc3.d and rc0.d folders.

3. I also created a symlink (just to make it easier) to /etc/init.d/mysql.server in /usr/bin/ named mysql.server.  This was done after the first steps failed to start MySQL (mostly to save typing).

"mysql.server start" and "mysql.server stop" work beautifully, but it does not appear to be starting on boot.

This is a 64-bit version of MySQL (5.1.45) on 64-bit Ubuntu Lucid Lynx (10.04), if it matters.

Obviously, I can work around this as it is on my desktop, but I would prefer not to have to.  Any help is greatly appreciated.

---

