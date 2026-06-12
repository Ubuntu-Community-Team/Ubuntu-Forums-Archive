---
title: "The PostgreSQL server failed to start."
date: 2010-02-12
forum: General Help
---

### Post by DedMoroz on 2010-02-12
I'm getting this error message every time I run updates. Any way to fix this? Thanks!

> dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postgresql-8.4
 postgresql


Also this...

> An error occurred

The following details are provided:

E: postgresql-8.4: subprocess installed post-installation script returned error exit status 1
E: postgresql: dependency problems - leaving unconfigured

---

### Post by DedMoroz on 2010-02-12
And more...

> Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  geoclue-localnet geoclue telepathy-salut wine1.2 libxmu-headers
  ttf-tahoma-replacement libsqlite0-dev libtelepathy-farsight0
  libtorrent-rasterbar5 geoclue-manual libxmu-dev geoclue-hostip
  telepathy-mission-control-5 ttf-symbol-replacement telepathy-gabble
  wine1.2-gecko libchamplain-0.4-0 libchamplain-gtk-0.4-0 liblcms1-dev
  libpq-dev libmpg123-0 libmng-dev miro-data geoclue-yahoo python-libtorrent
  empathy-common python-indicate
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.4 (8.4.2-0ubuntu9.10) ...
 * Starting PostgreSQL 8.4 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2010-02-12 09:43:48 PST LOG:  authentication option not in name=value format: sameuser

2010-02-12 09:43:48 PST CONTEXT:  line 74 of configuration file "/etc/postgresql/8.4/main/pg_hba.conf"
2010-02-12 09:43:48 PST FATAL:  could not load pg_hba.conf
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error processing postgresql-8.4 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 postgresql-8.4
 postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)

Im looking into the error codes as the guy here did (who solved the problem)...

[http://ubuntuforums.org/showthread.php?t=1363117](http://ubuntuforums.org/showthread.php?t=1363117)

---

### Post by DedMoroz on 2010-02-12
Unfortunately, I cant seem to figure out how he solved the problem as I know nothing about PostgreSQL!

---

### Post by DedMoroz on 2010-03-11
Still no luck on this one either. Ive contacted the author of the other thread with the same problem, but in a few weeks have yet to receive a reply. Would anyone have any insight into fixing this? Its quite annoying and every time I do an update this really slows things down.

Thanks for ANY help!

---

### Post by DedMoroz on 2010-03-11
Ive check Ubuntu's page regarding postgresql and checked every dependency to see if that was a prob. I have them all.

---

### Post by DedMoroz on 2010-03-11
Problem solved thanks to the Ubuntu IRC team.

I did this:

```
sudo apt-get remove --purge postgresql-8.4
```

then checked to see if pg_hba.conf still existed (it didnt)...

```
sudo gedit /etc/postgresql/8.4/main/pg_hba.conf
```

then went ahead and reinstalled postgresql via synaptic manager.

---

### Post by slevinfcross on 2010-10-10
> **DedMoroz said:**
> Problem solved thanks to the Ubuntu IRC team.

I did this:

```
sudo apt-get remove --purge postgresql-8.4
```

then checked to see if pg_hba.conf still existed (it didnt)...

```
sudo gedit /etc/postgresql/8.4/main/pg_hba.conf
```

then went ahead and reinstalled postgresql via synaptic manager.

Thank you very much. This helped me as well :)

---

