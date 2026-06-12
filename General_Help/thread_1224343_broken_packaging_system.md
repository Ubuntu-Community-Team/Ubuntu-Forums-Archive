---
title: "broken packaging system"
date: 2009-07-27
forum: General Help
---

### Post by bogdanbiv on 2009-07-27
When I try to install anything on my Kubuntu 9.04, I get the following error:
```
bogdanbiv@bogdanbiv-laptop:~$ sudo apt-get install speedcrunch
Reading package lists... Done
Building dependency tree
Reading state information... Done
speedcrunch is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

However, when I run '*apt-get -f install*', I get this:
```
bogdanbiv@bogdanbiv-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 62 not upgraded.
7 not fully installed or removed.
Need to get 0B/23.6MB of archives.
After this operation, 79.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 315348 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Funny thing is that I no longer wish to install MySQL-server-5.0, so how can I clean the system without '*apt-get -f install*'?

---

### Post by Choose on 2009-07-27
Try running 
```
sudo apt-get clean
```
that should delete everything in your apt cache ;)

---

### Post by bogdanbiv on 2009-07-27
Doesn't return anything and I still can't install any other packages.
```
bogdanbiv@bogdanbiv-laptop:~$ sudo apt-get install kgoldrunner
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Soul-Sing on 2009-07-27
If you already have 5.1 installed.(Do you really want to go back to 5.0?)
If you do, you'll need to uninstall 5.1 first.

> Aborting downgrade from (at least) 5.1 to 5.0.

Otherwise: ```
sudo apt-get -f install
```

---

### Post by bogdanbiv on 2009-07-27
At some point I had MySQL-5.1, but I think I unintentionally removed it when I installed akonadi-server (which requires version 5.0).

I did sudo apt-get remove mysql-server which removed the conflict and now I can install any package I want:

```
bogdanbiv@bogdanbiv-laptop:~$ sudo apt-get remove mysql-server
[sudo] password for bogdanbiv:                                
Reading package lists... Done                                 
Building dependency tree                                      
Reading state information... Done                             
The following packages were automatically installed and are no longer required:
  libhtml-template-perl                                                        
Use 'apt-get autoremove' to remove them.                                       
The following packages will be REMOVED:                                        
  mysql-server                                                                 
0 upgraded, 0 newly installed, 1 to remove and 62 not upgraded.                
7 not fully installed or removed.
```

But still there was another command that resolved conflicts by forcibly uninstalling offending software. Something like *dpkg --force-something*. Couldn't find it in dpkg manpage, though.

I think I'll install MariaDB now.

---

### Post by Soul-Sing on 2009-07-27
> Something like dpkg --force-something. Couldn't find it in dpkg manpage, though.

Something like: ```
sudo dpkg --remove --force-remove-reinstreq <name package>
```   ?

---

### Post by bogdanbiv on 2009-07-30
Yeap, that's it!
Thanks! 

Of course it was in the man page, it's me who couldn't see it.
Thanks again!

---

