---
title: "Packages Not in Ubuntu Universe?  (php5-sqlite3)"
date: 2006-06-15
forum: General Help
---

### Post by Sudrien on 2006-06-15
Not that I don't like Gentoo, its just there were times where it seemed I was in  Cold War with my machine...


I have just started on Xubuntu, thatough that should not matter too much for this question.

I would like to set up as a lighttpd+sqlite3+php5 installation. According to my research, php5-sqlite3 is one of the packages I need for this. But it ain't there, far as I can tell.

[http://utnubu.alioth.debian.org/binary-versiondiff.html](http://utnubu.alioth.debian.org/binary-versiondiff.html) confirms this - I think. That a debian packages exists, but an ubuntu one does not.

How might I proceed? 


-Sudrien.

---

### Post by blackjack6.21.91 on 2006-06-15
It seems to me that all three of those packages are in the Ubuntu repositories.  You might have to enable the multiverse repositories.
You can generate a sources.list from one of the links in my signature.

---

### Post by Sudrien on 2006-06-15
While those sources did give me some nice backages I was looking for, php5-sqlite3 was not one of them.

Note: php5-sqlite3 IS NOT php5-sqlite.

Is seems that simply nobody has taken the time to build the package.

[http://packages.debian.org/unstable/source/php-sqlite3](http://packages.debian.org/unstable/source/php-sqlite3) has a source package - could I build it off that?

-Sud.

---

### Post by dlpfmVfH on 2006-06-16
you could use my sources.list...
it has more then you need packages...including the php5.1pdo-sqlite
wich depends on libsqlite3-0

couldn't figure out from which repo it came..
so I included all 
You might find something usefull

greetz

---

### Post by Sudrien on 2006-06-16
Thank you, aboe.

The right repository line happened to be
```
deb http://people.debian.org/~dexter all dapper
```
apt-get install sqlite3
apt-get install php5.1-cgi 
apt-get install php-5.1pdo-sqlite 
apt-get install lighttpd


... going off the config at [http://www.xorg.us/news.php?10](http://www.xorg.us/news.php?10) too ...

but it gives me errors. So I'll try Php 5.0 and SQLite.

---

### Post by dlpfmVfH on 2006-06-16
ok, good luck then.

I tried, didn't tried the php5.1 packages...though...
just looked it up in synaptic

---

