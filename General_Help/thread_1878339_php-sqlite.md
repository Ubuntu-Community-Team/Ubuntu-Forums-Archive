---
title: "php-sqlite"
date: 2011-11-09
forum: General Help
---

### Post by arijitm on 2011-11-09
I am having a really hard time making my php5 installation in ubuntu to work with sqlite3. I can access sqlite3 from ubuntu terminal. My php seems to work fine too. But opening the /etc/php5/apache2/php.ini file I see 
[sqlite]
; [http://php.net/sqlite.assoc-case](http://php.net/sqlite.assoc-case)
;sqlite.assoc_case = 0

[sqlite3]
;sqlite3.extension_dir =
===============================================
and also php does not work with sqlite. I have tried a lot of solutions in a lot of forums, nothing worked. I do not know where exactly the problem is or what is missing. 

Can someone please help!!!!

---

### Post by marinara on 2011-11-11
you should try [this]("http://stackoverflow.com/questions/948899/how-to-enable-sqlite3-for-php"), to get the sqlite3 class installed into php

---

### Post by arijitm on 2011-11-12
I found this on web already. I tried it too. 
While

sudo apt-get install php5-cli php5-dev make
sudo apt-get install libsqlite3-0 libsqlite3-dev

works fine.. 

sudo apt-get install php5-sqlite3

This is where I get the message :: 

Package php5-sqlite3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php5-sqlite3 has no installation candidate

........................
I still executed the rest of the commands.. but to no use...

---

### Post by marinara on 2011-11-12
sudo apt-get install php5-sqlite

I don't have php installed in my Lubuntu vm, so haven't tested it.  Sounds like one of the package officers changed the name of the package

good luck

---

### Post by jesuspresley on 2012-08-09
> **marinara said:**
> sudo apt-get install php5-sqlite
This worked fine on my 10.04 VMware server. Helped me with my Symfony install, btw.

---

