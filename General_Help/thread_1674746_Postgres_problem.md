---
title: "Postgres problem"
date: 2011-01-24
forum: General Help
---

### Post by Nick Hopton on 2011-01-24
I am a fool with a problem. I installed PostgreSQL 9.0 (amd64), downloaded from the Enterprise site, configured it and added PostGIS. The installation was working perfectly with about 500-MB of spatial data imported to the databases.

But of course I couldn't leave well alone, so when I came across some instructions on the web about how to tune Postgres for improved PostGIS performance I just had to play (even though I am old enough to know better). The 'tuning' consisted of making changes to postgresql.conf, which I did and saved the changes. I was then not only unable to connect to the database, but unable even to start Postgres. Reversing the changes I made did not make any difference, Postgres still would not start.

I then decided to un-install Postgres and PostGIS, which I did. Un-installing left the data directory (/opt/PostgreSQL/9.0/data) intact but removed everything else, so far as I know. I then attempted to re-install Postgres, but the installation failed, which I guess might be something to do with the old configuration files left in the data directory.

So guys, where do I go from here? If necessary I'm prepared to blow the whole data directory away and start from scratch again, but I wonder if just deleting the .conf files would do?

I am a newcomer to Ubuntu (10.10, amd64) having previously used, you-know-what (I'm not sure if I'm allowed to mention the W-word here).

Any help would be gratefully received.

Regards, Nick

---

### Post by SeijiSensei on 2011-01-24
I hate to ask this, but did you dump the database first with pg_dump?  If so, then I'd say you should blow everything away and rebuild the database from the dump.  

If not, then I'd try first moving the existing data directory to another location ("mv /opt/PostgreSQL/9.0 /opt/PostgreSQL/bad/") and try installing again.  If that works, try moving the /data/ directory from the old installation into the new one and see what happens.

---

### Post by Nick Hopton on 2011-01-24
Thanks very much for this advice, it has got me out of trouble. As you suggested it would, moving the existing data directory allowed me to get a clean install of Postgres. To be honest I haven't tried importing the old databases, I still have the data that I imported and I'm bringing this back into my new databases. Oh the relief, I can't tell you :D .

Once again, many thanks.

Regards, Nick.

---

