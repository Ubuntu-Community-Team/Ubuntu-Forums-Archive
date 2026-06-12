---
title: "Postgres Error while installing any package"
date: 2012-02-14
forum: General Help
---

### Post by techbrainless on 2012-02-14
Hi ,

I used to get the following error(related to postgres database) while trying to install anything using apt-get command.


```
test@test-machine:/var/cache/apt/archives$ sudo apt-get install zip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zip is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-assistant libqt4-webkit virtuoso-nepomuk
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 3,904kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://security.ubuntu.com/ubuntu/ lucid-security/main postgresql-8.4 8.4.9-0ubuntu0.10.04 [3,904kB]
Fetched 3,904kB in 0s (11.4MB/s)   
(Reading database ... 395715 files and directories currently installed.)
Preparing to replace postgresql-8.4 8.4.9-0ubuntu0.10.04 (using .../postgresql-8.4_8.4.9-0ubuntu0.10.04_i386.deb) ...
 * Stopping PostgreSQL 8.4 database server                                                                                                                                                                         * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 63.
                                                                                                                                                                                                           [fail]
invoke-rc.d: initscript postgresql-8.4, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
 * Stopping PostgreSQL 8.4 database server                                                                                                                                                                         * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 63.
                                                                                                                                                                                                           [fail]
invoke-rc.d: initscript postgresql-8.4, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/postgresql-8.4_8.4.9-0ubuntu0.10.04_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 9
 * Starting PostgreSQL 8.4 database server                                                                                                                                                                         * Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 63.
                                                                                                                                                                                                           [fail]
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/postgresql-8.4_8.4.9-0ubuntu0.10.04_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
sources.list
```
$cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ye.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ye.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ye.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ye.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ye.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ye.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ye.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ye.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ye.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ye.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ye.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ye.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ye.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ye.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```I have tried to execute command like 
```
sudo apt-get clean autoclean 
```

delete the contents of archives and execute following commands
```
sudo mkdir -p /var/cache/apt/archives/partial 
sudo touch /var/cache/apt/archives/lock 
sudo chmod 640 /var/cache/apt/archives/lock 

```


but still facing the same issue

---

### Post by techbrainless on 2012-02-14
Hi All,

Any hint , any suggested solution ..........

---

### Post by cortman on 2012-02-14
How about deleting the problem package from the archive, so it will download and install a fresh version? Run

```
sudo apt-get purge postgresql-8.4
```

and then try to install whatever packages that gave the error.
It appears that something is wrong with the postgresql package in your deb archives, which is where Ubuntu will install from default, if the packages exist.
I'd say just rm the package itself, but I'm afraid you'd wind up with dependency problems, so try using apt-get.

---

### Post by techbrainless on 2012-02-14
Thanks cortman for your reply , 

I have followed your instructions in your reply , but does not work , I am still getting the same error!!!!!!!!!!!!!!!

---

### Post by cortman on 2012-02-14
Ok, run

```
sudo rm /var/cache/apt/archives/postgresql-8.4_8.4.9-0ubuntu0.10.04_i386.deb
```

then

```
sudo apt-get update
```

and try installing again.

---

### Post by techbrainless on 2012-02-14
Thanks cortman for your reply , 

I have tried the above 2 commands 

```
sudo rm /var/cache/apt/archives/postgresql-8.4_8.4.9-0ubuntu0.10.04_i386.deb
sudo apt-get update
```

but still getting the same error

---

### Post by cortman on 2012-02-14
OK, now that that's removed, run

```
sudo apt-get install -f
```

Which will scan the filesystem for broken packages and (is supposed to) fix them. Post any errors you get.

---

### Post by techbrainless on 2012-03-04
Thanks for your reply,

> sudo apt-get install -f
I have executed it but I am getting the same error

---

### Post by cortman on 2012-03-06
```
sudo apt-get clean
```

??

---

