---
title: "problems with phpmyadmin after upgrading to dapper"
date: 2006-06-04
forum: General Help
---

### Post by bloodroses75 on 2006-06-04
I had just recently upgraded from breezy to dapper via modifying the souces list and running synaptic. Overall, the upgrade went very well with only a few minor issues (icons dissapearing in rox-filer). However, there is one issue that I have now regarding phpmyadmin. When i try to access the page via locally, by remote computer, or by 127.0.0.1 I keep getting the same error:

**500 Internal Server Error**



**Internal Server Error**

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.0.55 (Ubuntu) DAV/2 mod_jk2/2.0.4 mod_ldap_userdir/1.1.8 PHP/5.1.2 mod_ruby/1.2.5 Ruby/1.8.4(2005-12-24) mod_perl/2.0.2 Perl/v5.8.7 Server at sunfire Port 80



Has anyone else had this problem after upgrading? If not, where is the server error log located at and what kind of issues should I be looking for? Kplaylist has an identical issue as well.

Thank you in advance.****

---

### Post by bloodroses75 on 2006-06-08
K... so far from what I've noticed, this error occurs on any account i use (even root), so I'm pretty sure its not a permissions error. I have tried a complete removal of phpmyadmin and then reinstalled it. The error still persists. However, all php scripts I have written before the upgrade still work, along with ones that require SQL access.

Should I also try complete removal/reinstalls of php and mysql? I do not want to have to rebuild my databases unless that is my only option. Also, could it be caused from a deb package I dont have installed (or even a bad one that is installed like php4 stuff)?

Any advice would be greatly appreciated

[COLOR="Red"]moving posts to forum link:[/COLOR]
[http://www.ubuntuforums.org/showthread.php?p=1114999]("http://www.ubuntuforums.org/showthread.php?p=1114999")

---

### Post by adamkane on 2006-06-09
Don't expect LAMP to "just work" after an upgrade from breezy to dapper.

Install LAMP this way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by mlind on 2006-06-09
What does the server logs say on /var/log/apache2/

---

### Post by bloodroses75 on 2006-06-12
k.. got the error log... this is the error that occurs every time i try to go to phpmyadmin
------------------

[Mon Jun 12 22:21:20 2006] [error] [client 127.0.0.1] Premature end of script headers: index.php, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Mon Jun 12 22:21:20 2006] [error] [client 127.0.0.1] SoftException in Application.cpp:193: Script "/var/www/phpmyadmin/index.php" resolving to "/usr/share/phpmyadmin/index.php" not within configured docroot, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Mon Jun 12 22:21:20 2006] [error] [client 127.0.0.1] *** glibc detected *** double free or corruption (fasttop): 0x0806fb38 ***, referer: [http://127.0.0.1/](http://127.0.0.1/)


and here is the error for kplaylist
------------------------------------------
[Mon Jun 12 22:24:38 2006] [error] [client 127.0.0.1] Premature end of script headers: kplaylist.1.6.401.php, referer: [http://127.0.0.1/kplaylist/](http://127.0.0.1/kplaylist/)
[Mon Jun 12 22:24:38 2006] [error] [client 127.0.0.1] SoftException in Application.cpp:233: Directory "/var/www/kplaylist" is writeable by group, referer: [http://127.0.0.1/kplaylist/](http://127.0.0.1/kplaylist/)
[Mon Jun 12 22:24:38 2006] [error] [client 127.0.0.1] *** glibc detected *** double free or corruption (fasttop): 0x0806fb18 ***, referer: [http://127.0.0.1/kplaylist/](http://127.0.0.1/kplaylist/)


i hope this gives some info. I noticed that im getting a premature end of script error on both situations, but I'm still not quite sure why.
And yes, i have tried to reinstall LAMP with the same result happening. :(

---

### Post by bloodroses75 on 2006-07-19
Finally got the problem fixed... the last set of patches for dapper corrected the issue.. I'm good to go now ... ty for the help :)

The thread can be closed now

---

### Post by cosmo1983 on 2006-07-26
Hi,

I am having problems trying to install phpmyadmin. I am new to ubuntu and not sure what I am doing wrong? Apache, php and mysql has installed properly.

"sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpmyadmin"

I keep getting this error, any help would be appreciated.

---

### Post by Rheuh on 2006-10-23
Hi Bloodroses75, I have the exact same problem after installing Ubuntu Server 6.06 and phpMyAdmin... the webserver configuration is correct, all my local sites work OK, except for phpMyAdmin where I keep getting this 500 internal server error, with the "not within configured docroot" in /var/log/apache2/error.log

I have tried to enable option "followsymlinks" for both /var/www/phpmyadmin and /usr/share/phpmyadmin in the configuration file /etc/apache2/sites.available/default, but it won't help... How did you fix this problem ? You said that the latest patches fixed it, but I have already done a "apt-get dist-upgrade" and there's no more patches I can apply...

Thanks in advance for helping a newbie admin ;)

-- Rheuh



PS: here's the /var/log/apache2/error.log :
```

[Mon Oct 23 19:13:06 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Mon Oct 23 19:13:15 2006] [error] [client 192.168.0.1] Premature end of script headers: index.php
[Mon Oct 23 19:13:15 2006] [error] [client 192.168.0.1] SoftException in Application.cpp:193: Script "/var/www/phpmyadmin/index.php" resolving to "/usr/share/phpmyadmin/index.php" not within configured docroot
[Mon Oct 23 19:13:15 2006] [error] [client 192.168.0.1] *** glibc detected *** double free or corruption (fasttop): 0x0806fa40 ***


```

---

### Post by adamantivm on 2006-12-23
Just in case it helps anybody, I had a very similar - if not exactly the same - problem and it was solved by removing all the suphp related packages I had installed on my system:

```

julian@zapatilla:/var/www$ sudo apt-get remove --purge suphp-common libapache2-mod-suphp
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libapache2-mod-suphp* suphp-common*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 401kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 147014 files and directories currently installed.)
Removing suphp-common ...
Purging configuration files for suphp-common ...
Removing libapache2-mod-suphp ...
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                                                                 [ ok ]
Purging configuration files for libapache2-mod-suphp ...
julian@zapatilla:/var/www$

```

After this, all my PHP stuff was back to normal - including following symlinks

---

### Post by TizzyD on 2007-07-03
Thanks for the catch there.  Why the incompatibility?  Not sure, but it should be documented.

---

### Post by Dragon-64 on 2007-11-24
Hey - \\:D/
I just wanted to say that I was also having problems with one of my php files working on my apache server! My error logs were as follows

[Sat Nov 24 09:05:31 2007] [error] [client 74.140.98.7] Premature end of script headers: chat.php, referer: [http://dragon64.homelinux.org/](http://dragon64.homelinux.org/)
[Sat Nov 24 09:05:32 2007] [error] [client 74.140.98.7] File does not exist: /var/www/favicon.ico
[Sat Nov 24 09:05:52 2007] [error] [client 74.140.98.7] SoftException in Application.cpp:239: Directory "/var/www" is writeable by group, referer: [http://dragon64.homelinux.org/](http://dragon64.homelinux.org/)

I then tried the suggested fix (sudo apt-get remove --purge suphp-common libapache2-mod-suphp) after trying this fix, my php file worked great!!
I do not know or understand yet why this fixed my problem, but I just wanted to say thanks a million for the fix if you ever come back and read this post!!

Dragon-64
---------------------------------------------------------------------
---------------------------------------------------------------------

> **adamantivm said:**
> Just in case it helps anybody, I had a very similar - if not exactly the same - problem and it was solved by removing all the suphp related packages I had installed on my system:

```

julian@zapatilla:/var/www$ sudo apt-get remove --purge suphp-common libapache2-mod-suphp
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libapache2-mod-suphp* suphp-common*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 401kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 147014 files and directories currently installed.)
Removing suphp-common ...
Purging configuration files for suphp-common ...
Removing libapache2-mod-suphp ...
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                                                                 [ ok ]
Purging configuration files for libapache2-mod-suphp ...
julian@zapatilla:/var/www$

```After this, all my PHP stuff was back to normal - including following symlinks

---

