---
title: "error while installing postfix?"
date: 2009-12-26
forum: General Help
---

### Post by conorcahir on 2009-12-26
Hi

after running 

"sudo apt-get install postfix"

I got the following output:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sensible-mda libmysqlclient15off m4 procmail sendmail-cf libreadline5
  sendmail-base
Use 'apt-get autoremove' to remove them.
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf
  postfix-cdb
The following packages will be REMOVED:
  sendmail-bin
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 1 to remove and 20 not upgraded.
Need to get 0B/1,380kB of archives.
After this operation, 1,483kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: sendmail-bin: dependency problems, but removing anyway as you requested:
 sensible-mda depends on sendmail-bin | mail-transport-agent; however:
  Package sendmail-bin is to be removed.
  Package mail-transport-agent is not installed.
  Package sendmail-bin which provides mail-transport-agent is to be removed.
 sensible-mda depends on sendmail-bin | mail-transport-agent; however:
  Package sendmail-bin is to be removed.
  Package mail-transport-agent is not installed.
  Package sendmail-bin which provides mail-transport-agent is to be removed.
(Reading database ... 160592 files and directories currently installed.)
Removing sendmail-bin ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Selecting previously deselected package postfix.
(Reading database ... 160544 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.6.5-3_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/postfix_2.6.5-3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.6.5-3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

now, I'm no expert, but I'm pretty sure something isn't right here. During a previous attempt to install postfix, the terminal crashed on a "choose configuration settings" screen so I had to kill the process before the installation was complete which i think is the reason for this line:

```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
```

any help would be appreciated

thanks

ps.

I also got this error during another previous attempt (after the crashed attempt but before the attempt referred to above):

```
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
```

which i fixed by deleting the lock file. The fact that both errors are to do with locks is what makes me think the crashed attempt is the cause of all this

---

### Post by dcstar on 2009-12-27
> **conorcahir said:**
> 
..........
```
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
```

which i fixed by deleting the lock file. The fact that both errors are to do with locks is what makes me think the crashed attempt is the cause of all this

Then delete that lock file.

---

### Post by conorcahir on 2009-12-27
which one? for the error i fixed the error message told me the name of the lock file 

           "could not get lock /var/cache/apt/archives/lock"

 which i simply deleted, whereas for the error i cannot fix the error message simply says that a file is locked by another process.

           "debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process:"

---

### Post by dcstar on 2009-12-27
> **conorcahir said:**
> which one? for the error i fixed the error message told me the name of the lock file 

           "could not get lock /var/cache/apt/archives/lock"

 which i simply deleted, whereas for the error i cannot fix the error message simply says that a file is locked by another process.

           "debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process:"

Use the System Monitor to search for that file to see what process has it open, or use:

```
lsof
```

---

### Post by conorcahir on 2009-12-28
restarting my computer seems to have solved the problem. Thanks anyway David

---

