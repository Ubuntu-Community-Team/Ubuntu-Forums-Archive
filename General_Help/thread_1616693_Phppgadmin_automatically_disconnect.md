---
title: "Phppgadmin automatically disconnect"
date: 2010-11-08
forum: General Help
---

### Post by manuelcano on 2010-11-08
Hi there,

I`ve just installed Xubuntu 10.10 and I installed phppgadmin on it but when I connect to postgres it automatically closes the session and I can not access the database. I tried via pgadmin3 graphically and there is not problem.

What could it be?

I appreciate your help.

Thanks

Manuel.

---

### Post by manuelcano on 2010-11-09
If somebody else has this problem, I solved it doing a downgrade of the php version trough this: [http://www.hipergalaxia.org/blog/tag/10-10/](http://www.hipergalaxia.org/blog/tag/10-10/). 

Plus the following commands:

sudo apt-get update
          sudo apt-get install php5-cli
          sudo apt-get install php5
          sudo apt-get install memcached
          sudo apt-get install php5-memcache
          sudo apt-get install php5-curl
          sudo apt-get install php5-pgsql

Manuel

---

