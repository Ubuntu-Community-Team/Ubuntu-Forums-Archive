---
title: "Kubuntu Dapper / kat crash"
date: 2006-05-31
forum: General Help
---

### Post by aurelieng on 2006-05-31
Hi all,

I installed kat 0.6.3 on my up to date Kubuntu Dapper in order to test it. When I run /usr/bin/kat, I see a wizard, but it unfortunately fails when trying to run the "kat daemon". Interestingly, when I run the /usr/bin/katdaemon manually, it seems to load properly, even though the wizard is still not able to see it.

After playing a bit, I saw several crashes both involving the katdaemon :
```
terminate called after throwing an instance of 'CppSQLite3Exception'
KCrash: Application 'katdaemon' crashing...
``` and kat itself:
```
*** glibc detected *** free(): invalid pointer: 0x081d4738 ***
KCrash: Application 'kat' crashing...
``` 
Ideas or feedback, anyone ?

Thx a lot, I'm very looking forward to testing it :D

---

### Post by mips on 2006-05-31
I don't use kat. Have you tried Kerry Beagle for KDE ?

---

### Post by aurelieng on 2006-05-31
"apt-get install kerry" is on its way.. I'm very looking forward to seeing how it compares with OS X's Spotlight :)

---

### Post by BooVeMan on 2006-10-25
If anyone is more inclined to kat - here is how to fix it:
use the default kat-0.6.3 package from drapper - this will happily crash sometimes even crashing kded... 
> terminate called after throwing an instance of 'CppSQLite3Exception' tipped me off, so I tried to update sqlite3.
Grab the sqlite-3.3.8 source tarball from [www.sqlite.org]("http://www.sqlite.org/download.html") untar it change into the sqlite-3.3.8 dir and do:
> ./configure --prefix=/usr 
make
sudo make install 
fire of the katdaemon and you are runing.
Good Luck!

---

