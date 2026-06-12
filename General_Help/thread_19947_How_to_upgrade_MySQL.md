---
title: "How to upgrade MySQL?"
date: 2005-03-14
forum: General Help
---

### Post by sbassi on 2005-03-14
I have the mysql server that is installed using Synaptic. that is: 4.0.20. I need to use 4.1.10 (because have data in that format in another machine).
Ubuntu doesn't seems to have that available in their repositories  ](*,) . But I found in Debian that they have it here:
[http://packages.debian.org/unstable/misc/mysql-server-4.1](http://packages.debian.org/unstable/misc/mysql-server-4.1) 
Is there a safe way to install it? I want to upgrade it from 4.0.20, don need both version installed at the same PC.

Best regards.
SB :p

---

### Post by jdong on 2005-03-14
It's best if you **compile** the Debian version, by grabbing the Source package (orig.tar.gz), and the Debian patch (.diff.gz).

Extract the orig.tar.gz file with tar -xzvf {FILENAME}, cd into the new directory, then run zcat ../mysql.diff.gz | patch -p1

then run chmod +x debian/rules, and **sudo dpkg-buildpackage**. If it complains about missing dependencies, install as many of them as you can with apt-get. If any are left that you can't satisfy, try to push on with the build: **sudo dpkg-buildpackage -d**. After compiling, do a "cd ..", and you should see a bunch of .deb's. Install them all, and you should have the new MySQL.

---

### Post by sbassi on 2005-03-14
hello, thank you for your fast answer. But, what about the old installation? Should I remove it first? (I have MySQL 4.0.20 working now).
Will the outlined procedure upgrade my MYSQL or just install another copy of it?

---

### Post by sbassi on 2005-03-14
[QUOTE=jdong]It's best if you **compile** the Debian version, by grabbing the Source package (orig.tar.gz), and the Debian patch (.diff.gz).

Extract the orig.tar.gz file with tar -xzvf {FILENAME}, cd into the new directory, then run zcat ../mysql.diff.gz | patch -p1

then run chmod +x debian/rules, and **sudo dpkg-buildpackage**. If it complains about missing dependencies, install as many of them as you can with apt-get. If any are left that you can't satisfy, try to push on with the build: **sudo dpkg-buildpackage -d**. After compiling, do a "cd ..", and you should see a bunch of .deb's. Install them all, and you should have the new MySQL.[/QUOTE]

After installed all requested dependencies,  I tried to make the buildpackage and I got this:

```

...some output deleted....
rm -rf patch-stamp patch-stampT debian/patched
rm -rf debian/patched
 dpkg-source -b mysql-dfsg-4.1-4.1.10a
dpkg-source: building mysql-dfsg-4.1 using existing mysql-dfsg-4.1_4.1.10a.orig.tar.gz
dpkg-source: building mysql-dfsg-4.1 in mysql-dfsg-4.1_4.1.10a-1.diff.gz
dpkg-source: warning: ignoring deletion of file scripts/mysqlbug
dpkg-source: building mysql-dfsg-4.1 in mysql-dfsg-4.1_4.1.10a-1.dsc
 debian/rules build
test -d debian/patched || install -d debian/patched
dpatch  apply  01_MAKEFILES__Docs_Images_Makefile.in 01_MAKEFILES__Docs_Makefile.in 02_scripts__Makfile.in__fill_help_tables 05_alpha 09_bdb__dist__configure__NO-POSIXMUTEX 13_configure__AMD64-LinuxThreads-vs-NPTL 17_man__mysqld__section 21_man__mysqldump 25_mysys__default.c 29_scripts__mysqlbug.sh 33_scripts__mysql_create_system_tables__no_test 37_scripts__mysqld_safe.sh__syslog 38_scripts__mysqld_safe.sh__signals 41_scripts__mysql_install_db.sh__no_test 45_warn-CLI-passwords 50_innodb_mixlen
applying patch 01_MAKEFILES__Docs_Images_Makefile.in to ./ .../usr/share/dpatch/dpatch-run: /usr/share/dpatch/dpatch-run: No such file or directory
 failed.
make: *** [patch-stamp] Error 1
```  

What is wrong? It seems it is looking for dpatch-run, but look what I got:


```
root@vicky2:/home/vicky/mysql-dfsg-4.1-4.1.10a # ls /usr/share/dpatch/
dpatch-edit-patch.functions  dpatch.make
root@vicky2:/home/vicky/mysql-dfsg-4.1-4.1.10a #
```

---

