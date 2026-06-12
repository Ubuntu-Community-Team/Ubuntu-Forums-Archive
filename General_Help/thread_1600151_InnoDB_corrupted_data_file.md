---
title: "InnoDB corrupted data file"
date: 2010-10-18
forum: General Help
---

### Post by gnapse on 2010-10-18
The following problem is happening in a Ubuntu Hardy 8.04 Server installed as a virtual machine on VMware. MySQL v5.0.51a.

After a power failure and the backup power supply exhausted, the host computer went off, and the vmware virtual one as well. When I started it everything started fine except MySQL.

When I try to start it the following error comes up in /var/log/syslog

```
Oct 18 12:22:36 www mysqld_safe[28740]: started
Oct 18 12:22:37 www mysqld[28744]: InnoDB: The log sequence number in ibdata files does not match
Oct 18 12:22:37 www mysqld[28744]: InnoDB: the log sequence number in the ib_logfiles!
Oct 18 12:22:37 www mysqld[28744]: 101018 12:22:37  InnoDB: Database was not shut down normally!
Oct 18 12:22:37 www mysqld[28744]: InnoDB: Starting crash recovery.
Oct 18 12:22:37 www mysqld[28744]: InnoDB: Reading tablespace information from the .ibd files...
Oct 18 12:22:37 www mysqld[28744]: InnoDB: Restoring possible half-written data pages from the doublewrite
Oct 18 12:22:37 www mysqld[28744]: InnoDB: buffer...
Oct 18 12:22:38 www mysqld[28744]: InnoDB: Error: trying to access page number 4294900607 in space 0,
Oct 18 12:22:38 www mysqld[28744]: InnoDB: space name ./ibdata1,
Oct 18 12:22:38 www mysqld[28744]: InnoDB: which is outside the tablespace bounds.
Oct 18 12:22:38 www mysqld[28744]: InnoDB: Byte offset 0, len 16384, i/o type 10.
```

That's the relevant part. Notice the part that says something about an error accesing some page number, which is outside the tablespace bounds.

The problem is clearly with the InnoDB engine, because when I disable InnoDB I can start the server, but of course all InnoDB tables are broken without InnoDB support.

I googled a little bit this error message, and I found this page about [starting the InnoDB engine in recovery mode]("http://dev.mysql.com/doc/refman/5.0/en/forcing-recovery.html"). I already tried with all recovery modes up to 6, and it did not work. Everytime I try to start the server I get the same error message.

Finally I downloaded this other [InnoDB recovery tool]("https://launchpad.net/percona-innodb-recovery-tool") but it seems it cannot work on the datafiles directly. Instead it relies on one's ability to actually start the server, in recovery mode if needed. But I am unable to start even in recovery mode, so I'm stuck.

Everything I've found out there about recovering InnoDB data assumes that switching to one of these recovery modes will at least allow you to start the server, but I haven't got there yet. Many sites even go as far as to say that Innodb recovery should be almost automatic and bring your database to consistent state without much intervention.

Is it possible that mine has gone corrupted beyond repair? Any ideas?

---

