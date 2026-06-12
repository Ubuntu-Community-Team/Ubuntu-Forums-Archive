---
title: "Finding PostgreSQL installed location"
date: 2011-03-24
forum: General Help
---

### Post by mdavidjohnson on 2011-03-24
I'm new to ubuntu and PostgreSQL. I'm using ubuntu 10.04 and PostgreSQL 8.4.7. I need to find out where PostgreSQL is located so I can run commands. 

I successfully installed PostgreSQL without changing any of the defaults. Matthew & Stones' *Beginning Databases with PosgreSQL From Novice to Professional*, as well as the PostgreSQL documentation, indicates the standard location is /usr/local/pgsql/bin/ but it's not there; it's somewhere else (ps -el | grep post confirms it IS running and psql is able to do \du to display the list of users and \l to display the list of databases).

But when I tried to create a new user by running /usr/local/pgsql/bin/createuser the command was not found.

I tried to locate the installation by running pg_config --bindir but it said pg_config was not installed. I downloaded pg_config and its dependencies and tried to install them with the package installer, but it wouldn't go because something is wrong with the libkrb5-3 and libkrb5support0 packages - they won't install and the package installer just zips through without reporting missing dependencies or anything. The MD5, SHA1, and SHA256 checksums all match, but they just won't install. I then tried the libk5crypto3 package just to make sure something wasn't wrong on my end - it installed fine.

So I searched the PostgreSQL FAQ and found out how to get the version without pg_config by doing a SELECT version(); query. Unfortunately, there appears to be no corresponding SELECT bindir(); query.

A plain ordinary file search for pgsql, postgresql, etc. was not very helpful either. 

Could somebody please point me to something which will help me discover PostgreSQL's actual installed location? (I'd check the install log but, of course, I can't find it either).

---

### Post by SeijiSensei on 2011-03-24
If you installed PostgreSQL from the Ubuntu repositories, all the user binaries are stored in /usr/bin and the server binaries in /usr/sbin.  This is the standard practice for all distributions if you install packages from their repositories.

The only time you'd end up with PostgreSQL (or other programs) in /usr/local is if you compiled the package yourself from its source code with the default configuration then installed it with "sudo make install".  Out-of-the-box /usr/local is empty (except for a directory structure) on Ubuntu and other mainstream distributions.  By convention, /usr/local is used for packages you install yourself outside of the repository structure.

So just get rid of the /usr/local/bin prefix and run "createuser," "psql," etc. from the command prompt.

BTW, you can determine the location of any files on your system using the locate command.  For instance, "locate psql" returns a list of all the [s]packages[/s] files with that string including "/usr/bin/psql".

---

### Post by mdavidjohnson on 2011-03-24
Thanks! That worked great. 

Any idea why the libkrb5-3 and libkrb5support0 packages won't install? I downloaded them from the ubuntu [security] repository, just like everything else I've installed (postgresql, apache, php, and drupal with all their dependencies) except for Python 3.2, which I built from source.

---

### Post by SeijiSensei on 2011-03-24
I don't use Kerberos, so I can't help you there.  You probably need to start a separate thread on that issue.

---

