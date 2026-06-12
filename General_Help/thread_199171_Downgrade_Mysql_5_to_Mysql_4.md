---
title: "Downgrade Mysql 5 to Mysql 4"
date: 2006-06-18
forum: General Help
---

### Post by funnyguyfunnyguy on 2006-06-18
I am trying to install MythTV on Ubuntu 6.06; however, I have ran into a problem running the mythfilldatabase. The problem is that the current version of MythTV in the repos .18, doesn't work with Mysql5, and the fix from .19 hasn't been backported to .18. Rather than compile .19, I would prefer to downgrade Mysql5 to Mysql4, but I haven't had any luck if finding out how to do that. Does anyone have any ideas?

---

### Post by Ramses de Norre on 2006-06-18
You'll need to find a way to convert your databases or delete and remake them all.. I had to do this too and I did the second way.
So in either case you'll need to run ```
sudo aptitude purge mysql-server mysql-common mysql-client && sudo aptitude install mysql-client-4.1 mysql-server-4.1
``` which will delete all your existing databases and install mysql 4.1.

---

### Post by mraudiofreak on 2006-06-18
hey-
good to see you're having the same problems, let me know when you fix it.

---

### Post by dxvxd on 2006-08-21
Trying to downgrade MySQL from 5.0 to 4.1 with this error:

```

Aborting downgrade from (at least) 5.0 to 4.1.
dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

Then delted downloaded file from /var/cache/apt/archives and tried again, but same error occured :(

---

### Post by Ramses de Norre on 2006-08-21
Your solution is above.. Maybe you could read the thread before posting in it.

---

### Post by dxvxd on 2006-08-21
> **Ramses de Norre said:**
> Your solution is above.. Maybe you could read the thread before posting in it.

I read it and did it before I post the problem.
in other words, the problem occured after i typed:

```
sudo aptitude purge mysql-server mysql-common mysql-client && sudo aptitude install mysql-client-4.1 mysql-server-4.1
```

---

### Post by Ramses de Norre on 2006-08-21
OK, I'm sorry then..
Can you do ```
mkdir ~/mysql_bak
sudo mv /var/lib/mysql/* ~/mysql_bak
```
And try purging and installing mysql again? This will move the mysql databases 5 which you'll need to regenerate with mysql 4.1.

---

### Post by rjgilligan on 2006-09-26
I was able to downgrade to 4.1 from 5 after removing /var/lib/mysql.  That solution works.

---

### Post by rjgilligan on 2006-09-26
yeah, what he said.

---

### Post by jonnymccullagh on 2008-01-18
worked for me (needed to downgrade mysql to get htcheck to work)
many thanks

---

