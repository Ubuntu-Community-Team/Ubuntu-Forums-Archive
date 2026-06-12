---
title: "how to list installed packages and version strings"
date: 2010-03-23
forum: General Help
---

### Post by miatawnt2b on 2010-03-23
I am able to see all of the installed packages using 'dpkg --get-selections' but it doesn't show the version number.  Is there a way to list my installed packages along with the version strings?

-J

---

### Post by patchwork on 2010-03-23
I think this is what you're looking for.

```
dpkg-query -W | less
```
More Info can be found with ```
man dpkg-query
```


Example from my system:
```
acpi-support    0.129
acpid   1.0.6-9ubuntu8
adduser 3.110ubuntu7
aisleriot       1:2.28.0-0ubuntu1
alacarte        0.12.4-0ubuntu2
alpine  2.00+dfsg-4ubuntu1
alsa-base       1.0.20+dfsg-1ubuntu5
alsa-utils      1.0.20-2ubuntu6
anacron 2.3-13.1ubuntu10
apache2 2.2.12-1ubuntu2.2
apache2-mpm-prefork     2.2.12-1ubuntu2.2
apache2-utils   2.2.12-1ubuntu2.2
apache2.2-bin   2.2.12-1ubuntu2.2
apache2.2-common        2.2.12-1ubuntu2.2

```

---

### Post by miatawnt2b on 2010-03-23
OK, I have a list of packages I need to uninstall, apt-get really wants to hose my system to do it.

Here's my issue.  I installed some packages from an unstable repo, and I now need to purge my currently installed packages and reinstall the ubuntu packages.  I have a file listing every package I need to remove and reinstall. However, due to dependencies, apt-get will want to also remove important stuff.  How can I do this?

THanks,
-J

---

### Post by patchwork on 2010-03-23
You could try this:

```
sudo dpkg -r --ignore-depends=packagename packagename
```

This will remove the package without removing dependencies.  For example, I removed mysql-client-5.0 without it's dependencies using

```
kevin@crystalpepsi:~$ dpkg --get-selections | grep mysql
libdbd-mysql-perl                install
libmysqlclient15off                install
libmysqlclient16                install
libqt4-sql-mysql                install
**mysql-client-5.0                install**
mysql-common                    install
mysql-server-5.0                install
mysql-server-core-5.0                install
php5-mysql                    install
r-cran-rmysql                    install
kevin@crystalpepsi:~$ sudo dpkg -r --ignore-depends=mysql-client-5.0 mysql-client-5.0
(Reading database ... 242561 files and directories currently installed.)
**Removing mysql-client-5.0 ...**
Processing triggers for man-db ...
kevin@crystalpepsi:~$ dpkg --get-selections | grep mysql
libdbd-mysql-perl                install
libmysqlclient15off                install
libmysqlclient16                install
libqt4-sql-mysql                install
mysql-common                    install
mysql-server-5.0                install
mysql-server-core-5.0                install
php5-mysql                    install
r-cran-rmysql                    install
kevin@crystalpepsi:~$ 

```

---

### Post by miatawnt2b on 2010-03-23
Thanks,
I ended up figuring this out...

*show installed packages and versions matching unstable and write to file
	apt-show-versions | grep unstable > unstable-packages

*separate out the package names
	cat unstable-packages | awk '{ print $1 }' > unstable-packages-parsed

*purge all packages from parsed and ignore dependencies
	cat unstable-packages-parsed | xargs sudo dpkg -P --force-depends

*re-install those packages
	cat unstable-packages-parsed | xargs sudo apt-get install

---

### Post by cmcanulty on 2010-05-10
Is there a way to print the list? I try select all & copy in terminal but it only selects 1st page I tried and the list started with m in the alphabet the above command ```
dpkg-query -W | less
```gave the whole list but won't let me select wholelist 
   ```
dpkg --list
```

---

