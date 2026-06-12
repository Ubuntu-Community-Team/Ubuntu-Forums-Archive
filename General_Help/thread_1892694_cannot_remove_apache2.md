---
title: "cannot remove apache2?"
date: 2011-12-08
forum: General Help
---

### Post by qwertyjjj on 2011-12-08
I am trying to install xampp but I had already installed apache2 and mysql so it won;t start.
I tried removing apache2 but it won't disappear.
Any ideas how to get rid of it?

```

j@j-Inspiron-9300:~$ sudo apt-get remove apache2
[sudo] password for j: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
j@j-Inspiron-9300:~$ /opt/lampp/lampp start
You need to start XAMPP as root!
j@j-Inspiron-9300:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.7...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
j@j-Inspiron-9300:~$

```

---

### Post by qwertyjjj on 2011-12-09
bump

---

### Post by Drenriza on 2011-12-09
```
sudo apt-get --remove  apache2
```
or
```
sudo apt-get --remove --purge apache2
```

--purge also removes configuration files

---

### Post by WorMzy on 2011-12-09
Removing the apache package doesn't stop the already running daemon. I recommend that you reboot.

---

### Post by Lars Noodén on 2011-12-09
A reboot is not necessary or desirable.  If the systemv script [font=Courier New]sudo /etc/init.d/apache2 stop[/font] does not work or has been removed, then the process can be killed manually using [pkill](http://manpages.ubuntu.com/manpages/oneiric/en/man1/pkill.1.html).

```

sudo pkill apache2

```

---

### Post by qwertyjjj on 2011-12-09
> **Drenriza said:**
> ```
sudo apt-get --remove  apache2
```
or
```
sudo apt-get --remove --purge apache2
```

--purge also removes configuration files

j@j-Inspiron-9300:~$ sudo apt-get --remove  apache2
E: Invalid operation apache2
j@j-Inspiron-9300:~$ sudo apt-get --remove --purge apache2
E: Invalid operation apache2

---

### Post by qwertyjjj on 2011-12-12
I ran sudo apt-get remove apache2
yet when I rebooted it had started again!

---

### Post by Lars Noodén on 2011-12-12
What method did you use to install Apache in the first place?

---

### Post by WorMzy on 2011-12-12
Are you sure that the apache that's starting isn't the one that this "XAMPP" comes with?

```
ps aux | grep 'apache\|http'
```

---

### Post by qwertyjjj on 2011-12-13
> **Lars Noodén said:**
> What method did you use to install Apache in the first place?

Ubuntu Software centre but I removed it from there also.

> **WorMzy said:**
> Are you sure that the apache that's starting isn't the one that this "XAMPP" comes with?

I'm pretty sure it's not because when I go to [http://localhost](http://localhost)
I get the apache error pages whereas when I start it up it's the xampp pages.

```
ps aux | grep 'apache\|http'
```

```

jason@jason-Inspiron-9300:~$ ps aux | grep 'apache\|http'
jason     2945  0.0  0.2  28388  5056 ?        Sl   07:36   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.13 /org/gtk/gvfs/exec_spaw/2
root      3526  0.2  0.9  54104 18796 ?        Ss   07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    3830  0.0  0.6  50168 12808 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    3896  0.0  0.7  54440 15964 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    3897  0.0  0.7  54104 14708 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    3898  0.0  0.7  54104 14708 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    3899  0.0  0.7  54104 14708 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    3900  0.0  0.7  54104 14708 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    3925  0.0  0.7  54104 14708 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
jason     3957  0.0  0.0   4016   744 pts/0    S+   07:45   0:00 grep --color=auto apache\|http
jason@jason-Inspiron-9300:~$ 


```

---

### Post by Lars Noodén on 2011-12-13
Where's this "XAMP" stuff coming from?  Several have been afflicted with it.  Was there an article on it somewhere?

```

nobody    3897  0.0  0.7  54104 14708 ?        S    07:44   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log

```

That's not where Apache gets installed if you install it from the Ubuntu repositories.  Nor is it the normal user.  

If you are lucky it was installed by a package and then it's just a matter of finding the name of the package. If it was not installed from a package then it needs uninstalling manually.

Try this to see which package it might belong to:

```

dpkg -S /opt/lampp/bin/httpd

```

If it returns a package name, then that's the one to uninstall.

---

### Post by MartijnNL on 2011-12-13
Considering /opt/lampp is not the normal install location for apache2 in the repositories, are you sure this is not the apache from xampp? How did you install xampp?

Also: in your previous post you gave a reply within a quote. That makes it easy to overlook.

---

### Post by qwertyjjj on 2011-12-13
> **MartijnNL said:**
> Considering /opt/lampp is not the normal install location for apache2 in the repositories, are you sure this is not the apache from xampp? How did you install xampp?

Also: in your previous post you gave a reply within a quote. That makes it easy to overlook.

It is yes, I installed xampp following their website process.
I issue the command /opt/lampp/lampp restart
but it will never restart as it says ANOTHER httpd is already running

```

j@j-Inspiron-9300:~$ dpkg -S /opt/lampp/bin/httpd
dpkg: /opt/lampp/bin/httpd not found.

```

---

### Post by Lars Noodén on 2011-12-13
> **qwertyjjj said:**
> It is yes, I installed xampp following their website process.


Can you post the URL to that process so we can see what it was?  That will help clarify how to uninstall it.  If we are lucky, then it was provided as a package and not just a tarball or something similar.

For what it's worth, mixing unpackaged applications on a system can quickly make a mess.  Been there, done that.

---

### Post by MartijnNL on 2011-12-13
> **Lars Noodén said:**
> Can you post the URL to that process so we can see what it was?  That will help clarify how to uninstall it.  If we are lucky, then it was provided as a package and not just a tarball or something similar.

For what it's worth, mixing unpackaged applications on a system can quickly make a mess.  Been there, done that.

As far as I can tell he doesn't want to uninstall Xampp. But xampp seems to claim there's another httpd running. But based on the ps aux output it seems to me that the only httpd that's running is the one from xampp itself (/opt/lampp/bin/httpd).

The only thing is that there are multiple instances of /opt/lampp/bin/httpd running. That in itself is normal, but maybe the "/opt/lampp/lampp restart" command has a problem with it.

It seems to me that this is a problem related to the xampp install itself, so maybe they have their own support?

---

### Post by qwertyjjj on 2011-12-13
> **Lars Noodén said:**
> Can you post the URL to that process so we can see what it was?  That will help clarify how to uninstall it.  If we are lucky, then it was provided as a package and not just a tarball or something similar.

For what it's worth, mixing unpackaged applications on a system can quickly make a mess.  Been there, done that.

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

> **MartijnNL said:**
> As far as I can tell he doesn't want to uninstall Xampp. But xampp seems to claim there's another httpd running. But based on the ps aux output it seems to me that the only httpd that's running is the one from xampp itself (/opt/lampp/bin/httpd).

The only thing is that there are multiple instances of /opt/lampp/bin/httpd running. That in itself is normal, but maybe the "/opt/lampp/lampp restart" command has a problem with it.

It seems to me that this is a problem related to the xampp install itself, so maybe they have their own support?

That's the problem. But everytime I do it, to get it running I do this:
sudo pkill apache2
opt/lampp/lampp restart

after a restart it has reappeared:
```

j@j-Inspiron-9300:~$ ps aux | grep 'apache\|http'
root      1501  0.0  0.1   5356  2392 ?        Ss   11:53   0:00 /usr/sbin/apache2 -k start
root      1503  0.0  0.0   5356  1484 ?        S    11:53   0:00 /usr/sbin/apache2 -k start
root      1504  0.0  0.0   5356  1484 ?        S    11:53   0:00 /usr/sbin/apache2 -k start
root      1505  0.0  0.0   5356  1484 ?        S    11:53   0:00 /usr/sbin/apache2 -k start
root      1506  0.0  0.0   5356  1484 ?        S    11:53   0:00 /usr/sbin/apache2 -k start
root      1507  0.0  0.0   5356  1484 ?        S    11:53   0:00 /usr/sbin/apache2 -k start
j         2384  0.0  0.0   4016   740 pts/0    S+   11:55   0:00 grep --color=auto apache\|http
jason@jason-Inspiron-9300:~$ sudo apt-get remove apache2
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
**0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.**

jason@jason-Inspiron-9300:~$ sudo pkill apache2
jason@jason-Inspiron-9300:~$ sudo /opt/lampp/lampp restart
Stopping XAMPP for Linux 1.7.7...
XAMPP: XAMPP-Apache is not running.
XAMPP: XAMPP-MySQL is not running.
XAMPP: XAMPP-ProFTPD is not running.
XAMPP stopped.
Starting XAMPP for Linux 1.7.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

jason@jason-Inspiron-9300:~$ ps aux | grep 'apache\|http'
jason     2443  0.0  0.2  28372  4832 ?        Sl   11:57   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.13 /org/gtk/gvfs/exec_spaw/2
root      2571  3.5  0.9  54104 18804 ?        Ss   12:02   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    2862  0.0  0.6  50168 12808 ?        S    12:02   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    2947  0.0  0.7  54104 14708 ?        S    12:02   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    2948  0.0  0.7  54104 14708 ?        S    12:02   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    2949  0.0  0.7  54104 14708 ?        S    12:02   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    2950  0.0  0.7  54104 14708 ?        S    12:02   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
nobody    2951  0.0  0.7  54104 14708 ?        S    12:02   0:00 /opt/lampp/bin/httpd -k start -DSSL -DPHP5 -E /opt/lampp/logs/error_log
jason     3001  0.0  0.0   4016   740 pts/0    S+   12:02   0:00 grep --color=auto apache\|http



```

---

### Post by Lars Noodén on 2011-12-13
> **qwertyjjj said:**
> [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

Ok.  Thanks.  Everything provided by that tarball can be better provided via Ubuntu's repositories.  In fact, some items, like perl, are part of the default installation already.  By installing "XAMPP" you end up with a second, conflicting copy of perl.  You also end up with a [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) server, which is insecure, instead of a secure SFTP server.  My recommendation would be to carefully uninstall "XAMPP" from [font=Courier New]/opt[/font] and add the following packages from the repository:

[list]
[*] apache2
[*] openssh-server
[*] php5
[*] mysql-server
[/list]

Only the first two are really necessary unless you are specifically planning on doing something in PHP and MySQL.

PS Can I ask how you heard of the "XAMPP" tarball and decided to download it?

---

### Post by qwertyjjj on 2011-12-13
> **Lars Noodén said:**
> Ok.  Thanks.  Everything provided by that tarball can be better provided via Ubuntu's repositories.  In fact, some items, like perl, are part of the default installation already.  By installing "XAMPP" you end up with a second, conflicting copy of perl.  You also end up with a [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) server, which is insecure, instead of a secure SFTP server.  My recommendation would be to carefully uninstall "XAMPP" from [font=Courier New]/opt[/font] and add the following packages from the repository:

[list]
[*] apache2
[*] openssh-server
[*] php5
[*] mysql-server
[/list]

Only the first two are really necessary unless you are specifically planning on doing something in PHP and MySQL.

PS Can I ask how you heard of the "XAMPP" tarball and decided to download it?

As far as I knew, xampp was the better choice. Lampp and xampp have been around quite a while and much easier to set up a development machine on than installing everything separately. That is unless apache2 conflicts.

But I'm still not sure why apache2 keeps reappearing?
and yes, I need a fully functioning web server with PHP and MySQL.

---

### Post by Lars Noodén on 2011-12-13
> **qwertyjjj said:**
> 

But I'm still not sure why apache2 keeps reappearing?

I looked at the tarball and it dumps everything under ./lampp, in your case /opt/lampp, so I can't see where or how it could be automatically starting Apache.  You should be able to manually stop it : /opt/lampp/lampp stop

The way it appears set up, it seems that the Ubuntu packages have much better security defaults.

Speaking of security, automated security updates would be another reason to use Ubuntu's packages.  Otherwise, you'll have to manually go through the XAMPP installation each time you find out about the need for a security update in Apache, MySQL, PHP & PEAR, Perl, ProFTPD, phpMyAdmin, OpenSSL, GD, Freetype2, libjpeg, libpng, gdbm, zlib, expat, Sablotron, libxml, Ming, Webalizer, pdf class, ncurses, mod_perl, FreeTDS, gettext, mcrypt, mhash, eAccelerator, SQLite or IMAP C-Client.  Most seriously, the package management system is probably the [single biggest advancement](http://ianmurdock.com/solaris/how-package-management-changed-everything/) that Linux has brought to IT.

You might also be able to stop it manually this way:

```

sudo pkill -x httpd

```

---

### Post by MartijnNL on 2011-12-13
I agree with Lars that installing the individual packages using apt/Software Center/Synaptic is a much better approach. Yes, you may need to do some manual configuration for apache, mysql and php, but this is minor compared to all the work of maintaining the packages manually. It would probably take less time than you have invested in this problem.

Apart from that: Just to make sure: you are running ubuntu aren't you? And which ubuntu version are you running?

Also could you post the output of:

```
find / -path "/opt*" -prune -o -name "*apache*" 2> /dev/null
```

Just to see which files with apache in their names exist on your system (excluding the /opt directory).

---

### Post by WorMzy on 2011-12-13
Rather than installing individual packages, I'd just install lamp-server^

```
sudo apt-get install lamp-server^
```

I assume that still works.



It looks like the package that provides /usr/sbin/apache2 is still installed, or else your system has gone quite, quite mad.

Can you run

```
dpkg-query -S /usr/sbin/apache2
``` and post the output here.

Also, make it clear whether you'd rather continue using this XAMPP thing, or switch to using the officially supported packages.

---

### Post by qwertyjjj on 2011-12-13
ason@jason-Inspiron-9300:~$ find / -path "/opt*" -prune -o -name "*apache*" 2> /dev/null
/opt
/var/cache/apt/archives/apache2_2.2.16-1ubuntu3.4_i386.deb
/var/cache/apt/archives/apache2.2-bin_2.2.16-1ubuntu3.4_i386.deb
/var/cache/apt/archives/apache2-utils_2.2.16-1ubuntu3.4_i386.deb
/var/cache/apt/archives/libapache2-mod-php5filter_5.3.3-1ubuntu9.6_i386.deb
/var/cache/apt/archives/apache2-mpm-worker_2.2.16-1ubuntu3.4_i386.deb
/var/cache/apt/archives/apache2.2-common_2.2.16-1ubuntu3.4_i386.deb
/var/cache/apt/archives/apache2-mpm-itk_2.2.16-1ubuntu3.4_i386.deb
/var/cache/apt/archives/libapache2-mod-php5_5.3.3-1ubuntu9.6_i386.deb
/var/cache/apt/archives/apache2-mpm-prefork_2.2.16-1ubuntu3.4_i386.deb
/var/cache/apache2
/var/run/apache2
/var/lib/update-rc.d/apache2
/var/lib/dpkg/info/libapache2-mod-php5filter.conffiles
/var/lib/dpkg/info/apache2.2-common.md5sums
/var/lib/dpkg/info/libapache2-mod-php5filter.prerm
/var/lib/dpkg/info/apache2-mpm-itk.postinst
/var/lib/dpkg/info/apache2.2-bin.md5sums
/var/lib/dpkg/info/libapache2-mod-php5filter.triggers
/var/lib/dpkg/info/libapache2-mod-php5filter.postinst
/var/lib/dpkg/info/apache2-utils.md5sums
/var/lib/dpkg/info/apache2.2-common.postrm
/var/lib/dpkg/info/apache2.2-common.postinst
/var/lib/dpkg/info/apache2-mpm-itk.prerm
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5filter.md5sums
/var/lib/dpkg/info/apache2.2-common.preinst
/var/lib/dpkg/info/apache2.2-bin.list
/var/lib/dpkg/info/apache2.2-common.list
/var/lib/dpkg/info/apache2-mpm-itk.preinst
/var/lib/dpkg/info/apache2-mpm-itk.md5sums
/var/lib/dpkg/info/apache2-mpm-itk.list
/var/lib/dpkg/info/libapache2-mod-php5filter.list
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/apache2-utils.list
/var/lib/dpkg/info/apache2.2-common.conffiles
/var/lib/dpkg/info/libapache2-mod-php5filter.postrm
/var/lock/apache2
/var/log/apache2
/usr/sbin/apache2
/usr/sbin/apachectl
/usr/sbin/apache2ctl
/usr/share/apache2
/usr/share/apache2/icons/apache_pb.png
/usr/share/apache2/icons/apache_pb2.png
/usr/share/apache2/icons/apache_pb2_ani.gif
/usr/share/apache2/icons/apache_pb.gif
/usr/share/apache2/icons/apache_pb2.gif
/usr/share/man/man8/apachectl.8.gz
/usr/share/man/man8/apache2.8.gz
/usr/share/man/man8/apache2ctl.8.gz
/usr/share/bug/apache2.2-common
/usr/share/bug/apache2-mpm-itk
/usr/share/doc/apache2.2-bin
/usr/share/doc/librpc-xml-perl/README.apache2
/usr/share/doc/apache2-utils
/usr/share/doc/libapache2-mod-php5filter
/usr/share/doc/apache2.2-common
/usr/share/doc/apache2.2-common/examples/apache2
/usr/share/doc/apache2.2-common/examples/apache2/apache2.conf.gz
/usr/share/doc/apache2.2-common/examples/apache2.monit
/usr/share/doc/apache2-mpm-itk
/usr/share/kde4/apps/katepart/syntax/apache.xml
/usr/share/lintian/overrides/libapache2-mod-php5filter
/usr/share/lintian/overrides/apache2.2-common
/usr/share/lintian/overrides/apache2-mpm-itk
/usr/lib/apache2
/usr/lib/apache2/mpm-itk/apache2
/usr/lib/apache2/mpm-event/apache2
/usr/lib/apache2/mpm-prefork/apache2
/usr/lib/apache2/mpm-worker/apache2
/etc/apparmor.d/abstractions/apache2-common
/etc/cron.daily/apache2
/etc/apache2
/etc/apache2/apache2.conf
/etc/rc0.d/K09apache2
/etc/ufw/applications.d/apache2.2-common
/etc/rc1.d/K09apache2
/etc/init.d/apache2
/etc/rc6.d/K09apache2
/etc/php5/apache2
/etc/php5/apache2filter
/etc/rc4.d/S91apache2
/etc/default/apache2
/etc/rc5.d/S91apache2
/etc/logrotate.d/apache2
/etc/bash_completion.d/apache2.2-common
/etc/bash_completion.d/apache2ctl
/etc/rc2.d/S91apache2
/etc/rc3.d/S91apache2





jason@jason-Inspiron-9300:~$ dpkg-query -S /usr/sbin/apache2
apache2-mpm-itk: /usr/sbin/apache2

I don't mind. I just wanted a quick system and read in a few places that xampp was easy to get going.
I'd just like to understand why apache won't uninstall?! :)

---

### Post by manofwar95 on 2011-12-13
```
/etc/init.d/apache2 stop
```
```
sudo apt-get remove apache2
```

---

### Post by MartijnNL on 2011-12-13
@ manofwar95: please read a tread before replying. The OP has already tried that.

@qwertyjjj

Try uninstalling apache2-mpm-itk:

```
sudo apt-get remove apache2-mpm-itk
```

optionally followed by

```
sudo apt-get autoremove
```

to remove all no longer needed dependencies.

In addition: could you also post the output of:

```
dpkg -l apache*
```

You might want to uninstall packages listed there. Starting with:

```
sudo apt-get remove apache2.2-bin apache2.2-common
```

and then running 

```
 sudo apt-get autoremove
```

again. That should get rid of everything.

The apache2 packages is just a metapackage which causes other relevant packages to be installed. It seems that in your case the other packages were installed in some other way. So you'll need to remove them manually as well. Do you by any chance have installed another piece of software which might have caused apache to be installed? Like gnome-user-share for example? Or webmin?

It might be that other components like mysql are installed double as well.

And my excuses for all the edits. I just keep coming up with new ideas.

---

### Post by qwertyjjj on 2011-12-13
> **MartijnNL said:**
> @ manofwar95: please read a tread before replying. The OP has already tried that.

@qwertyjjj

Try uninstalling apache2-mpm-itk:

```
sudo apt-get remove apache2-mpm-itk
```

optionally followed by

```
sudo apt-get autoremove
```

to remove all no longer needed dependencies.

In addition: could you also post the output of:

```
dpkg -l apache*
```

You might want to uninstall packages listed there. Starting with:

```
sudo apt-get remove apache2.2-bin apache2.2-common
```

and then running 

```
 sudo apt-get autoremove
```

again. That should get rid of everything.

The apache2 packages is just a metapackage which causes other relevant packages to be installed. It seems that in your case the other packages were installed in some other way. So you'll need to remove them manually as well. Do you by any chance have installed another piece of software which might have caused apache to be installed? Like gnome-user-share for example? Or webmin?

It might be that other components like mysql are installed double as well.

And my excuses for all the edits. I just keep coming up with new ideas.

ran all those, now am left with:

jason@jason-Inspiron-9300:~$ dpkg -l apache*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  apache         <none>         (no description available)
un  apache-common  <none>         (no description available)
un  apache-utils   <none>         (no description available)
un  apache2        <none>         (no description available)
un  apache2-common <none>         (no description available)
un  apache2-doc    <none>         (no description available)
un  apache2-mpm    <none>         (no description available)
un  apache2-mpm-ev <none>         (no description available)
ii  apache2-mpm-it 2.2.16-1ubuntu multiuser MPM for Apache 2.2
un  apache2-mpm-pe <none>         (no description available)
un  apache2-mpm-pr <none>         (no description available)
un  apache2-mpm-th <none>         (no description available)
un  apache2-mpm-wo <none>         (no description available)
un  apache2-suexec <none>         (no description available)
un  apache2-suexec <none>         (no description available)
ii  apache2-utils  2.2.16-1ubuntu utility programs for webservers
ii  apache2.2-bin  2.2.16-1ubuntu Apache HTTP Server common binary files
ii  apache2.2-comm 2.2.16-1ubuntu Apache HTTP Server common files
jason@jason-Inspiron-9300:~$

---

### Post by MartijnNL on 2011-12-13
Well you probably got rid of most. I now realise you could have run

```
sudo apt-get remove apache* && sudo apt-get autoremove
```

You can still to this to remove the rest. Or if you want to remove it's configuration files as well, use

```
sudo apt-get purge apache* && sudo apt-get autoremove
```

Please be aware that you have probably also uninstalled the package which caused apache to be installed in the first place, like webmin for example. Whether this is a problem depends on how apache got installed. But you'll notice it when something else stops working. If that is a problem you might want to remove the xampp install and go for the manual install of packages (or the lamp-server) as mentioned earlier in this thread.

---

### Post by qwertyjjj on 2011-12-13
> **MartijnNL said:**
> Well you probably got rid of most. I now realise you could have run

```
sudo apt-get remove apache* && sudo apt-get autoremove
```

You can still to this to remove the rest. Or if you want to remove it's configuration files as well, use

```
sudo apt-get purge apache* && sudo apt-get autoremove
```

Please be aware that you have probably also uninstalled the package which caused apache to be installed in the first place, like webmin for example. Whether this is a problem depends on how apache got installed. But you'll notice it when something else stops working. If that is a problem you might want to remove the xampp install and go for the manual install of packages (or the lamp-server) as mentioned earlier in this thread.

hmm, still some packages remaining. seems apache is about as clingy as internet explorer :)

```

jason@jason-Inspiron-9300:~$ sudo apt-get remove apache* && sudo apt-get autoremove
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'apache2' for regex 'apache*'
Note, selecting 'apache2-mpm-worker' for regex 'apache*'
Note, selecting 'apache2-mpm-prefork' for regex 'apache*'
Note, selecting 'apache2-mpm-event' for regex 'apache*'
Note, selecting 'apache2-mpm-itk' for regex 'apache*'
Note, selecting 'apache2.2-common' for regex 'apache*'
Note, selecting 'apache2-doc' for regex 'apache*'
Note, selecting 'apache2.2-bin' for regex 'apache*'
Note, selecting 'apache2-common' for regex 'apache*'
Note, selecting 'apache2-mpm' for regex 'apache*'
Note, selecting 'apache2-mpm-perchild' for regex 'apache*'
Note, selecting 'apache2-mpm-threadpool' for regex 'apache*'
Note, selecting 'apache2-prefork-dev' for regex 'apache*'
Note, selecting 'apache2-threaded-dev' for regex 'apache*'
Note, selecting 'apache2-dev' for regex 'apache*'
Note, selecting 'apache2-utils' for regex 'apache*'
Note, selecting 'apache-common' for regex 'apache*'
Note, selecting 'apache-utils' for regex 'apache*'
Note, selecting 'apache2-suexec' for regex 'apache*'
Note, selecting 'apache2-suexec-custom' for regex 'apache*'
Note, selecting 'apache' for regex 'apache*'
Note, selecting 'libapache-mod-perl' for regex 'apache*'
Note, selecting 'libapache2-mod-axis2c' for regex 'apache*'
Note, selecting 'libapache-mod-auth-kerb' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-kerb' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-mysql' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-pgsql' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-plain' for regex 'apache*'
Note, selecting 'libapache2-mod-macro' for regex 'apache*'
Note, selecting 'libapache2-mod-perl2' for regex 'apache*'
Note, selecting 'libapache2-reload-perl' for regex 'apache*'
Note, selecting 'libapache2-mod-perl2-dev' for regex 'apache*'
Note, selecting 'libapache2-mod-perl2-doc' for regex 'apache*'
Note, selecting 'libapache2-mod-php5' for regex 'apache*'
Note, selecting 'libapache2-mod-php4' for regex 'apache*'
Note, selecting 'libapache2-mod-php5filter' for regex 'apache*'
Note, selecting 'libapache2-mod-python' for regex 'apache*'
Note, selecting 'libapache2-mod-python-doc' for regex 'apache*'
Note, selecting 'libapache-mod-python' for regex 'apache*'
Note, selecting 'libapache-mod-python2.1' for regex 'apache*'
Note, selecting 'libapache-mod-python2.2' for regex 'apache*'
Note, selecting 'libapache-mod-python2.3' for regex 'apache*'
Note, selecting 'libapache2-mod-python2.2' for regex 'apache*'
Note, selecting 'libapache2-mod-python2.3' for regex 'apache*'
Note, selecting 'libapache2-mod-python2.4' for regex 'apache*'
Note, selecting 'libapache2-mod-python2.6' for regex 'apache*'
Note, selecting 'libapache2-mod-wsgi' for regex 'apache*'
Note, selecting 'libapache2-mod-log-sql-dbi' for regex 'apache*'
Note, selecting 'libapache2-mod-scgi' for regex 'apache*'
Note, selecting 'gforge-web-apache2' for regex 'apache*'
Note, selecting 'apachetop' for regex 'apache*'
Note, selecting 'mono-apache-server1' for regex 'apache*'
Note, selecting 'mono-apache-server2' for regex 'apache*'
Note, selecting 'apache-ssl' for regex 'apache*'
Note, selecting 'apache-perl' for regex 'apache*'
Note, selecting 'libapache2-mod-lisp' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-openid' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-pam' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-radius' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-shadow' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-sys-group' for regex 'apache*'
Note, selecting 'libapache2-mod-log-sql-mysql' for regex 'apache*'
Note, selecting 'libapache2-mod-bwshare' for regex 'apache*'
Note, selecting 'libapache-singleton-perl' for regex 'apache*'
Note, selecting 'gforge-web-apache2-vhosts' for regex 'apache*'
Note, selecting 'libapache-mod-php5' for regex 'apache*'
Note, selecting 'libapache-mod-php4' for regex 'apache*'
Note, selecting 'gforge-web-apache' for regex 'apache*'
Note, selecting 'libapache2-mod-dnssd' for regex 'apache*'
Note, selecting 'libapache-mod-ruby' for regex 'apache*'
Note, selecting 'libapache2-mod-ruby' for regex 'apache*'
Note, selecting 'libapache-admin-config-perl' for regex 'apache*'
Note, selecting 'libapache-asp-perl' for regex 'apache*'
Note, selecting 'libapache-ssi-perl' for regex 'apache*'
Note, selecting 'libapache-authenhook-perl' for regex 'apache*'
Note, selecting 'libapache-authznetldap-perl' for regex 'apache*'
Note, selecting 'libapache-configfile-perl' for regex 'apache*'
Note, selecting 'libapache-db-perl' for regex 'apache*'
Note, selecting 'libapache-dbi-perl' for regex 'apache*'
Note, selecting 'libapache-dbilogger-perl' for regex 'apache*'
Note, selecting 'libapache-gallery-perl' for regex 'apache*'
Note, selecting 'libapache-request-perl' for regex 'apache*'
Note, selecting 'libapache-htpasswd-perl' for regex 'apache*'
Note, selecting 'libapache-mime4j-java' for regex 'apache*'
Note, selecting 'libapache-mime4j-java-doc' for regex 'apache*'
Note, selecting 'libapache-mod-jk-doc' for regex 'apache*'
Note, selecting 'libapache2-mod-jk' for regex 'apache*'
Note, selecting 'libapache-mod-jk' for regex 'apache*'
Note, selecting 'libapache-mod-security' for regex 'apache*'
Note, selecting 'libapache2-mod-security2' for regex 'apache*'
Note, selecting 'libapache-ruby1.8' for regex 'apache*'
Note, selecting 'libapache-session-perl' for regex 'apache*'
Note, selecting 'libapache-session-wrapper-perl' for regex 'apache*'
Note, selecting 'libapache-sessionx-perl' for regex 'apache*'
Note, selecting 'libapache2-authcassimple-perl' for regex 'apache*'
Note, selecting 'libapache2-request-perl' for regex 'apache*'
Note, selecting 'libapache2-authenntlm-perl' for regex 'apache*'
Note, selecting 'libapache2-mod-apparmor' for regex 'apache*'
Note, selecting 'libapache2-mod-apreq2' for regex 'apache*'
Note, selecting 'libapache2-mod-auth-cas' for regex 'apache*'
Note, selecting 'libapache2-mod-authn-sasl' for regex 'apache*'
Note, selecting 'libapache2-mod-authnz-external' for regex 'apache*'
Note, selecting 'libapache2-mod-authz-unixgroup' for regex 'apache*'
Note, selecting 'libapache2-mod-bw' for regex 'apache*'
Note, selecting 'libapache2-mod-chroot' for regex 'apache*'
Note, selecting 'libapache2-mod-defensible' for regex 'apache*'
Note, selecting 'libapache2-mod-encoding' for regex 'apache*'
Note, selecting 'libapache2-mod-evasive' for regex 'apache*'
Note, selecting 'libapache2-mod-fcgid' for regex 'apache*'
Note, selecting 'libapache2-mod-fcgid-dbg' for regex 'apache*'
Note, selecting 'libapache2-mod-geoip' for regex 'apache*'
Note, selecting 'libapache2-mod-gnutls' for regex 'apache*'
Note, selecting 'libapache2-mod-jk2' for regex 'apache*'
Note, selecting 'libapache2-mod-layout' for regex 'apache*'
Note, selecting 'libapache2-mod-ldap-userdir' for regex 'apache*'
Note, selecting 'libapache2-mod-log-sql' for regex 'apache*'
Note, selecting 'libapache2-mod-log-sql-ssl' for regex 'apache*'
Note, selecting 'libapache2-mod-mime-xattr' for regex 'apache*'
Note, selecting 'libapache2-mod-mono' for regex 'apache*'
Note, selecting 'mono-apache-server' for regex 'apache*'
Note, selecting 'libapache2-mod-musicindex' for regex 'apache*'
Note, selecting 'libapache2-mod-neko' for regex 'apache*'
Note, selecting 'libapache2-mod-ocamlnet' for regex 'apache*'
Note, selecting 'libapache2-mod-passenger' for regex 'apache*'
Note, selecting 'libapache2-mod-proxy-html' for regex 'apache*'
Note, selecting 'libapache2-mod-random' for regex 'apache*'
Note, selecting 'libapache2-mod-removeip' for regex 'apache*'
Note, selecting 'libapache2-mod-rpaf' for regex 'apache*'
Note, selecting 'libapache2-mod-shib2' for regex 'apache*'
Note, selecting 'libapache2-mod-shib' for regex 'apache*'
Note, selecting 'libapache2-mod-spamhaus' for regex 'apache*'
Note, selecting 'libapache2-mod-speedycgi' for regex 'apache*'
Note, selecting 'libapache2-mod-suphp' for regex 'apache*'
Note, selecting 'libapache2-mod-vhost-hash-alias' for regex 'apache*'
Note, selecting 'libapache2-mod-vhost-ldap' for regex 'apache*'
Note, selecting 'libapache2-mod-xsendfile' for regex 'apache*'
Note, selecting 'libapache2-modxslt' for regex 'apache*'
Note, selecting 'libapache2-redirtoservname' for regex 'apache*'
Note, selecting 'libapache2-svn' for regex 'apache*'
Note, selecting 'libapache2-webauth' for regex 'apache*'
Note, selecting 'libapache2-webkdc' for regex 'apache*'
Note, selecting 'libcatalyst-engine-apache-perl' for regex 'apache*'
Note, selecting 'libconfig-apacheformat-perl' for regex 'apache*'
Note, selecting 'libmasonx-request-withapachesession-perl' for regex 'apache*'
Note, selecting 'mahara-apache2' for regex 'apache*'
Note, selecting 'mahara-apache' for regex 'apache*'
Note, selecting 'libapache-mod-musicindex' for regex 'apache*'
Note, selecting 'python-apache-openid' for regex 'apache*'
Note, selecting 'apache-openid' for regex 'apache*'
Note, selecting 'rt3.8-apache2' for regex 'apache*'
Note, selecting 'libapache2-mod-fastcgi' for regex 'apache*'
Note, selecting 'torrus-apache' for regex 'apache*'
Note, selecting 'torrus-apache2' for regex 'apache*'
Note, selecting 'centrifydc-apache' for regex 'apache*'
Note, selecting 'webmin-apache' for regex 'apache*'
Note, selecting 'apache2-threaded-dev' instead of 'apache2-dev'
Note, selecting 'libapache2-mod-python' instead of 'libapache2-mod-python2.6'
Note, selecting 'libapache-mod-security' instead of 'libapache2-mod-security2'
Package libapache-mod-auth-kerb is not installed, so not removed
Package libapache2-mod-auth-kerb is not installed, so not removed
Package libapache2-mod-auth-mysql is not installed, so not removed
Package libapache2-mod-auth-pgsql is not installed, so not removed
Package libapache2-mod-auth-plain is not installed, so not removed
Package libapache2-mod-axis2c is not installed, so not removed
Package libapache2-mod-macro is not installed, so not removed
Package libapache2-mod-perl2 is not installed, so not removed
Package libapache2-mod-perl2-dev is not installed, so not removed
Package libapache2-mod-perl2-doc is not installed, so not removed
Package libapache2-mod-python is not installed, so not removed
Package libapache2-mod-python-doc is not installed, so not removed
Package libapache2-mod-wsgi is not installed, so not removed
Package libapache2-reload-perl is not installed, so not removed
Package apachetop is not installed, so not removed
Package gforge-web-apache is not installed, so not removed
Package gforge-web-apache2 is not installed, so not removed
Package gforge-web-apache2-vhosts is not installed, so not removed
Package libapache-admin-config-perl is not installed, so not removed
Package libapache-asp-perl is not installed, so not removed
Package libapache-authenhook-perl is not installed, so not removed
Package libapache-authznetldap-perl is not installed, so not removed
Package libapache-configfile-perl is not installed, so not removed
Package libapache-db-perl is not installed, so not removed
Package libapache-dbi-perl is not installed, so not removed
Package libapache-dbilogger-perl is not installed, so not removed
Package libapache-gallery-perl is not installed, so not removed
Package libapache-htpasswd-perl is not installed, so not removed
Package libapache-mime4j-java is not installed, so not removed
Package libapache-mime4j-java-doc is not installed, so not removed
Package libapache-mod-jk-doc is not installed, so not removed
Package libapache-mod-security is not installed, so not removed
Package libapache-ruby1.8 is not installed, so not removed
Package libapache-session-perl is not installed, so not removed
Package libapache-session-wrapper-perl is not installed, so not removed
Package libapache-sessionx-perl is not installed, so not removed
Package libapache-singleton-perl is not installed, so not removed
Package libapache2-authcassimple-perl is not installed, so not removed
Package libapache2-authenntlm-perl is not installed, so not removed
Package libapache2-mod-apreq2 is not installed, so not removed
Package libapache2-mod-auth-cas is not installed, so not removed
Package libapache2-mod-auth-openid is not installed, so not removed
Package libapache2-mod-auth-pam is not installed, so not removed
Package libapache2-mod-auth-radius is not installed, so not removed
Package libapache2-mod-auth-sys-group is not installed, so not removed
Package libapache2-mod-authn-sasl is not installed, so not removed
Package libapache2-mod-authz-unixgroup is not installed, so not removed
Package libapache2-mod-bw is not installed, so not removed
Package libapache2-mod-chroot is not installed, so not removed
Package libapache2-mod-defensible is not installed, so not removed
Package libapache2-mod-dnssd is not installed, so not removed
Package libapache2-mod-encoding is not installed, so not removed
Package libapache2-mod-evasive is not installed, so not removed
Package libapache2-mod-geoip is not installed, so not removed
Package libapache2-mod-gnutls is not installed, so not removed
Package libapache2-mod-jk is not installed, so not removed
Package libapache2-mod-layout is not installed, so not removed
Package libapache2-mod-ldap-userdir is not installed, so not removed
Package libapache2-mod-lisp is not installed, so not removed
Package libapache2-mod-log-sql is not installed, so not removed
Package libapache2-mod-log-sql-dbi is not installed, so not removed
Package libapache2-mod-log-sql-mysql is not installed, so not removed
Package libapache2-mod-log-sql-ssl is not installed, so not removed
Package libapache2-mod-mime-xattr is not installed, so not removed
Package libapache2-mod-mono is not installed, so not removed
Package libapache2-mod-musicindex is not installed, so not removed
Package libapache2-mod-neko is not installed, so not removed
Package libapache2-mod-ocamlnet is not installed, so not removed
Package libapache2-mod-passenger is not installed, so not removed
Package libapache2-mod-proxy-html is not installed, so not removed
Package libapache2-mod-random is not installed, so not removed
Package libapache2-mod-removeip is not installed, so not removed
Package libapache2-mod-rpaf is not installed, so not removed
Package libapache2-mod-ruby is not installed, so not removed
Package libapache2-mod-scgi is not installed, so not removed
Package libapache2-mod-shib2 is not installed, so not removed
Package libapache2-mod-spamhaus is not installed, so not removed
Package libapache2-mod-speedycgi is not installed, so not removed
Package libapache2-mod-suphp is not installed, so not removed
Package libapache2-mod-vhost-hash-alias is not installed, so not removed
Package libapache2-mod-vhost-ldap is not installed, so not removed
Package libapache2-mod-xsendfile is not installed, so not removed
Package libapache2-modxslt is not installed, so not removed
Package libapache2-redirtoservname is not installed, so not removed
Package libapache2-request-perl is not installed, so not removed
Package libapache2-webauth is not installed, so not removed
Package libapache2-webkdc is not installed, so not removed
Package libcatalyst-engine-apache-perl is not installed, so not removed
Package libconfig-apacheformat-perl is not installed, so not removed
Package libmasonx-request-withapachesession-perl is not installed, so not removed
Package mono-apache-server is not installed, so not removed
Package mono-apache-server1 is not installed, so not removed
Package mono-apache-server2 is not installed, so not removed
Package python-apache-openid is not installed, so not removed
Package torrus-apache is not installed, so not removed
Package torrus-apache2 is not installed, so not removed
Package apache2 is not installed, so not removed
Package apache2-doc is not installed, so not removed
Package apache2-mpm-event is not installed, so not removed
Package apache2-mpm-worker is not installed, so not removed
Package apache2-prefork-dev is not installed, so not removed
Package apache2-threaded-dev is not installed, so not removed
Package apache2-mpm-itk is not installed, so not removed
Package apache2-suexec is not installed, so not removed
Package apache2-suexec-custom is not installed, so not removed
Package libapache2-mod-apparmor is not installed, so not removed
Package libapache2-mod-authnz-external is not installed, so not removed
Package libapache2-mod-fcgid is not installed, so not removed
Package libapache2-mod-fcgid-dbg is not installed, so not removed
Package libapache2-mod-php5filter is not installed, so not removed
Package libapache2-svn is not installed, so not removed
Package mahara-apache2 is not installed, so not removed
Package rt3.8-apache2 is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 apache2-mpm-prefork : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.4) but it is not going to be installed
 apache2.2-common : Depends: apache2.2-bin (= 2.2.16-1ubuntu3.4) but it is not going to be installed
                    Depends: apache2-utils but it is not going to be installed
E: Broken packages
jason@jason-Inspiron-9300:~$ dpkg -l apache*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  apache         <none>         (no description available)
un  apache-common  <none>         (no description available)
un  apache-utils   <none>         (no description available)
un  apache2        <none>         (no description available)
un  apache2-common <none>         (no description available)
un  apache2-doc    <none>         (no description available)
un  apache2-mpm    <none>         (no description available)
un  apache2-mpm-ev <none>         (no description available)
un  apache2-mpm-it <none>         (no description available)
un  apache2-mpm-pe <none>         (no description available)
ii  apache2-mpm-pr 2.2.16-1ubuntu Apache HTTP Server - traditional non-threade
un  apache2-mpm-th <none>         (no description available)
un  apache2-mpm-wo <none>         (no description available)
un  apache2-suexec <none>         (no description available)
un  apache2-suexec <none>         (no description available)
ii  apache2-utils  2.2.16-1ubuntu utility programs for webservers
ii  apache2.2-bin  2.2.16-1ubuntu Apache HTTP Server common binary files
ii  apache2.2-comm 2.2.16-1ubuntu Apache HTTP Server common files
jason@jason-Inspiron-9300:~$ 


```

---

### Post by qwertyjjj on 2011-12-13
the purge seemed to work:

jason@jason-Inspiron-9300:~$ dpkg -l apache*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  apache         <none>         (no description available)
un  apache-common  <none>         (no description available)
un  apache-utils   <none>         (no description available)
un  apache2        <none>         (no description available)
un  apache2-common <none>         (no description available)
un  apache2-doc    <none>         (no description available)
un  apache2-mpm    <none>         (no description available)
un  apache2-mpm-ev <none>         (no description available)
un  apache2-mpm-it <none>         (no description available)
un  apache2-mpm-pe <none>         (no description available)
un  apache2-mpm-pr <none>         (no description available)
un  apache2-mpm-th <none>         (no description available)
un  apache2-mpm-wo <none>         (no description available)
un  apache2-suexec <none>         (no description available)
un  apache2-suexec <none>         (no description available)
un  apache2-utils  <none>         (no description available)
un  apache2.2-bin  <none>         (no description available)
un  apache2.2-comm <none>         (no description available)
jason@jason-Inspiron-9300:~$

**THANKS ALL!!!!!**

---

### Post by MartijnNL on 2011-12-13
You're welcome. Nice to see that it worked.

Did you mark the thread as Solved using the Tread Tools on top?

---

### Post by qwertyjjj on 2011-12-17
One more issue.
Apache is removed but now the update manager appears every so often and wants to reinstall apache and a load of utils.
Why would that happen when it is not installed?

---

### Post by satanselbow on 2011-12-17
> **qwertyjjj said:**
> One more issue.
Apache is removed but now the update manager appears every so often and wants to reinstall apache and a load of utils.
Why would that happen when it is not installed?

You may have something that relies on apache still installed as a dependency (part of xammp possibly or phpmyadmin?)

The code below will give you paths to any apache2 related files left behind - you could try the same for xammp or it's components. You may need to install dlocate 1st as it is not installed by default.

```
dlocate -S apache2
```

---

### Post by qwertyjjj on 2011-12-18
> **satanselbow said:**
> You may have something that relies on apache still installed as a dependency (part of xammp possibly or phpmyadmin?)

The code below will give you paths to any apache2 related files left behind - you could try the same for xammp or it's components. You may need to install dlocate 1st as it is not installed by default.

```
dlocate -S apache2
```

I was pretty sure I'd uninstalled these already though ?confused?

```

apache2.2-common: /etc/apache2/apache2.conf
apache2.2-common: /etc/apache2/envvars
apache2.2-common: /etc/apache2/magic
apache2.2-common: /etc/apache2/mods-available
apache2.2-common: /etc/apache2/mods-available/cern_meta.load
apache2.2-common: /etc/apache2/mods-available/ext_filter.load
apache2.2-common: /etc/apache2/mods-available/actions.load
apache2.2-common: /etc/apache2/mods-available/deflate.load
apache2.2-common: /etc/apache2/mods-available/setenvif.load
apache2.2-common: /etc/apache2/mods-available/authz_default.load
apache2.2-common: /etc/apache2/mods-available/cgi.load
apache2.2-common: /etc/apache2/mods-available/dir.load
apache2.2-common: /etc/apache2/mods-available/log_forensic.load
apache2.2-common: /etc/apache2/mods-available/ldap.load
apache2.2-common: /etc/apache2/mods-available/dir.conf
apache2.2-common: /etc/apache2/mods-available/proxy_connect.load
apache2.2-common: /etc/apache2/mods-available/status.conf
apache2.2-common: /etc/apache2/mods-available/proxy_balancer.conf
apache2.2-common: /etc/apache2/mods-available/authn_anon.load
apache2.2-common: /etc/apache2/mods-available/authz_dbm.load
apache2.2-common: /etc/apache2/mods-available/info.conf
apache2.2-common: /etc/apache2/mods-available/file_cache.load
apache2.2-common: /etc/apache2/mods-available/authn_default.load
apache2.2-common: /etc/apache2/mods-available/disk_cache.conf
apache2.2-common: /etc/apache2/mods-available/autoindex.load
apache2.2-common: /etc/apache2/mods-available/proxy_ajp.load
apache2.2-common: /etc/apache2/mods-available/filter.load
apache2.2-common: /etc/apache2/mods-available/proxy_http.load
apache2.2-common: /etc/apache2/mods-available/alias.conf
apache2.2-common: /etc/apache2/mods-available/mime.load
apache2.2-common: /etc/apache2/mods-available/headers.load
apache2.2-common: /etc/apache2/mods-available/authz_groupfile.load
apache2.2-common: /etc/apache2/mods-available/userdir.load
apache2.2-common: /etc/apache2/mods-available/version.load
apache2.2-common: /etc/apache2/mods-available/info.load
apache2.2-common: /etc/apache2/mods-available/usertrack.load
apache2.2-common: /etc/apache2/mods-available/mem_cache.load
apache2.2-common: /etc/apache2/mods-available/setenvif.conf
apache2.2-common: /etc/apache2/mods-available/speling.load
apache2.2-common: /etc/apache2/mods-available/cgid.load
apache2.2-common: /etc/apache2/mods-available/rewrite.load
apache2.2-common: /etc/apache2/mods-available/substitute.load
apache2.2-common: /etc/apache2/mods-available/ssl.load
apache2.2-common: /etc/apache2/mods-available/negotiation.conf
apache2.2-common: /etc/apache2/mods-available/proxy_balancer.load
apache2.2-common: /etc/apache2/mods-available/status.load
apache2.2-common: /etc/apache2/mods-available/authnz_ldap.load
apache2.2-common: /etc/apache2/mods-available/ssl.conf
apache2.2-common: /etc/apache2/mods-available/mime_magic.load
apache2.2-common: /etc/apache2/mods-available/authn_dbm.load
apache2.2-common: /etc/apache2/mods-available/dav.load
apache2.2-common: /etc/apache2/mods-available/dav_lock.load
apache2.2-common: /etc/apache2/mods-available/authz_owner.load
apache2.2-common: /etc/apache2/mods-available/auth_digest.load
apache2.2-common: /etc/apache2/mods-available/reqtimeout.conf
apache2.2-common: /etc/apache2/mods-available/reqtimeout.load
apache2.2-common: /etc/apache2/mods-available/autoindex.conf
apache2.2-common: /etc/apache2/mods-available/proxy.conf
apache2.2-common: /etc/apache2/mods-available/dav_fs.conf
apache2.2-common: /etc/apache2/mods-available/authz_host.load
apache2.2-common: /etc/apache2/mods-available/dav_fs.load
apache2.2-common: /etc/apache2/mods-available/proxy.load
apache2.2-common: /etc/apache2/mods-available/auth_basic.load
apache2.2-common: /etc/apache2/mods-available/imagemap.load
apache2.2-common: /etc/apache2/mods-available/asis.load
apache2.2-common: /etc/apache2/mods-available/proxy_scgi.load
apache2.2-common: /etc/apache2/mods-available/proxy_ftp.load
apache2.2-common: /etc/apache2/mods-available/vhost_alias.load
apache2.2-common: /etc/apache2/mods-available/userdir.conf
apache2.2-common: /etc/apache2/mods-available/deflate.conf
apache2.2-common: /etc/apache2/mods-available/mem_cache.conf
apache2.2-common: /etc/apache2/mods-available/cgid.conf
apache2.2-common: /etc/apache2/mods-available/env.load
apache2.2-common: /etc/apache2/mods-available/mime_magic.conf
apache2.2-common: /etc/apache2/mods-available/authn_dbd.load
apache2.2-common: /etc/apache2/mods-available/suexec.load
apache2.2-common: /etc/apache2/mods-available/include.load
apache2.2-common: /etc/apache2/mods-available/ident.load
apache2.2-common: /etc/apache2/mods-available/disk_cache.load
apache2.2-common: /etc/apache2/mods-available/charset_lite.load
apache2.2-common: /etc/apache2/mods-available/dbd.load
apache2.2-common: /etc/apache2/mods-available/negotiation.load
apache2.2-common: /etc/apache2/mods-available/expires.load
apache2.2-common: /etc/apache2/mods-available/ldap.conf
apache2.2-common: /etc/apache2/mods-available/dump_io.load
apache2.2-common: /etc/apache2/mods-available/actions.conf
apache2.2-common: /etc/apache2/mods-available/cache.load
apache2.2-common: /etc/apache2/mods-available/mime.conf
apache2.2-common: /etc/apache2/mods-available/proxy_ftp.conf
apache2.2-common: /etc/apache2/mods-available/unique_id.load
apache2.2-common: /etc/apache2/mods-available/authn_alias.load
apache2.2-common: /etc/apache2/mods-available/authn_file.load
apache2.2-common: /etc/apache2/mods-available/alias.load
apache2.2-common: /etc/apache2/mods-available/authz_user.load
apache2.2-common: /etc/apache2/ports.conf
apache2.2-common: /etc/apache2/sites-available
apache2.2-common: /etc/apache2/sites-available/default
apache2.2-common: /etc/apache2/sites-available/default-ssl
apache2.2-common: /etc/bash_completion.d/apache2.2-common
apache2.2-common: /etc/logrotate.d/apache2
apache2.2-common: /etc/ufw/applications.d/apache2.2-common
apache2.2-common: /etc/default/apache2
apache2.2-common: /etc/init.d/apache2
apache2.2-common: /etc/cron.daily/apache2
apache2.2-common: /usr/share/apache2
apache2.2-common: /usr/share/apache2/build
apache2.2-common: /usr/share/apache2/build/envvars-std
apache2.2-common: /usr/share/apache2/default-site
apache2.2-common: /usr/share/apache2/default-site/index.html
apache2.2-common: /usr/share/apache2/icons
apache2.2-common: /usr/share/apache2/icons/README
apache2.2-common: /usr/share/apache2/icons/README.html
apache2.2-common: /usr/share/apache2/icons/a.gif
apache2.2-common: /usr/share/apache2/icons/a.png
apache2.2-common: /usr/share/apache2/icons/alert.black.gif
apache2.2-common: /usr/share/apache2/icons/alert.black.png
apache2.2-common: /usr/share/apache2/icons/alert.red.gif
apache2.2-common: /usr/share/apache2/icons/alert.red.png
apache2.2-common: /usr/share/apache2/icons/apache_pb.gif
apache2.2-common: /usr/share/apache2/icons/apache_pb.png
apache2.2-common: /usr/share/apache2/icons/apache_pb2.gif
apache2.2-common: /usr/share/apache2/icons/apache_pb2.png
apache2.2-common: /usr/share/apache2/icons/apache_pb2_ani.gif
apache2.2-common: /usr/share/apache2/icons/back.gif
apache2.2-common: /usr/share/apache2/icons/back.png
apache2.2-common: /usr/share/apache2/icons/ball.gray.gif
apache2.2-common: /usr/share/apache2/icons/ball.gray.png
apache2.2-common: /usr/share/apache2/icons/ball.red.gif
apache2.2-common: /usr/share/apache2/icons/ball.red.png
apache2.2-common: /usr/share/apache2/icons/binary.gif
apache2.2-common: /usr/share/apache2/icons/binary.png
apache2.2-common: /usr/share/apache2/icons/binhex.gif
apache2.2-common: /usr/share/apache2/icons/binhex.png
apache2.2-common: /usr/share/apache2/icons/blank.gif
apache2.2-common: /usr/share/apache2/icons/blank.png
apache2.2-common: /usr/share/apache2/icons/bomb.gif
apache2.2-common: /usr/share/apache2/icons/bomb.png
apache2.2-common: /usr/share/apache2/icons/box1.gif
apache2.2-common: /usr/share/apache2/icons/box1.png
apache2.2-common: /usr/share/apache2/icons/box2.gif
apache2.2-common: /usr/share/apache2/icons/box2.png
apache2.2-common: /usr/share/apache2/icons/broken.gif
apache2.2-common: /usr/share/apache2/icons/broken.png
apache2.2-common: /usr/share/apache2/icons/burst.gif
apache2.2-common: /usr/share/apache2/icons/burst.png
apache2.2-common: /usr/share/apache2/icons/c.gif
apache2.2-common: /usr/share/apache2/icons/c.png
apache2.2-common: /usr/share/apache2/icons/comp.blue.gif
apache2.2-common: /usr/share/apache2/icons/comp.blue.png
apache2.2-common: /usr/share/apache2/icons/comp.gray.gif
apache2.2-common: /usr/share/apache2/icons/comp.gray.png
apache2.2-common: /usr/share/apache2/icons/compressed.gif
apache2.2-common: /usr/share/apache2/icons/compressed.png
apache2.2-common: /usr/share/apache2/icons/continued.gif
apache2.2-common: /usr/share/apache2/icons/continued.png
apache2.2-common: /usr/share/apache2/icons/dir.gif
apache2.2-common: /usr/share/apache2/icons/dir.png
apache2.2-common: /usr/share/apache2/icons/diskimg.gif
apache2.2-common: /usr/share/apache2/icons/diskimg.png
apache2.2-common: /usr/share/apache2/icons/down.gif
apache2.2-common: /usr/share/apache2/icons/down.png
apache2.2-common: /usr/share/apache2/icons/dvi.gif
apache2.2-common: /usr/share/apache2/icons/dvi.png
apache2.2-common: /usr/share/apache2/icons/f.gif
apache2.2-common: /usr/share/apache2/icons/f.png
apache2.2-common: /usr/share/apache2/icons/folder.gif
apache2.2-common: /usr/share/apache2/icons/folder.open.gif
apache2.2-common: /usr/share/apache2/icons/folder.open.png
apache2.2-common: /usr/share/apache2/icons/folder.png
apache2.2-common: /usr/share/apache2/icons/folder.sec.gif
apache2.2-common: /usr/share/apache2/icons/folder.sec.png
apache2.2-common: /usr/share/apache2/icons/forward.gif
apache2.2-common: /usr/share/apache2/icons/forward.png
apache2.2-common: /usr/share/apache2/icons/generic.gif
apache2.2-common: /usr/share/apache2/icons/generic.png
apache2.2-common: /usr/share/apache2/icons/generic.red.gif
apache2.2-common: /usr/share/apache2/icons/generic.red.png
apache2.2-common: /usr/share/apache2/icons/generic.sec.gif
apache2.2-common: /usr/share/apache2/icons/generic.sec.png
apache2.2-common: /usr/share/apache2/icons/hand.right.gif
apache2.2-common: /usr/share/apache2/icons/hand.right.png
apache2.2-common: /usr/share/apache2/icons/hand.up.gif
apache2.2-common: /usr/share/apache2/icons/hand.up.png
apache2.2-common: /usr/share/apache2/icons/icon.sheet.gif
apache2.2-common: /usr/share/apache2/icons/icon.sheet.png
apache2.2-common: /usr/share/apache2/icons/image1.gif
apache2.2-common: /usr/share/apache2/icons/image1.png
apache2.2-common: /usr/share/apache2/icons/image2.gif
apache2.2-common: /usr/share/apache2/icons/image2.png
apache2.2-common: /usr/share/apache2/icons/image3.gif
apache2.2-common: /usr/share/apache2/icons/image3.png
apache2.2-common: /usr/share/apache2/icons/index.gif
apache2.2-common: /usr/share/apache2/icons/index.png
apache2.2-common: /usr/share/apache2/icons/layout.gif
apache2.2-common: /usr/share/apache2/icons/layout.png
apache2.2-common: /usr/share/apache2/icons/left.gif
apache2.2-common: /usr/share/apache2/icons/left.png
apache2.2-common: /usr/share/apache2/icons/link.gif
apache2.2-common: /usr/share/apache2/icons/link.png
apache2.2-common: /usr/share/apache2/icons/movie.gif
apache2.2-common: /usr/share/apache2/icons/movie.png
apache2.2-common: /usr/share/apache2/icons/p.gif
apache2.2-common: /usr/share/apache2/icons/p.png
apache2.2-common: /usr/share/apache2/icons/patch.gif
apache2.2-common: /usr/share/apache2/icons/patch.png
apache2.2-common: /usr/share/apache2/icons/pdf.gif
apache2.2-common: /usr/share/apache2/icons/pdf.png
apache2.2-common: /usr/share/apache2/icons/pie0.gif
apache2.2-common: /usr/share/apache2/icons/pie0.png
apache2.2-common: /usr/share/apache2/icons/pie1.gif
apache2.2-common: /usr/share/apache2/icons/pie1.png
apache2.2-common: /usr/share/apache2/icons/pie2.gif
apache2.2-common: /usr/share/apache2/icons/pie2.png
apache2.2-common: /usr/share/apache2/icons/pie3.gif
apache2.2-common: /usr/share/apache2/icons/pie3.png
apache2.2-common: /usr/share/apache2/icons/pie4.gif
apache2.2-common: /usr/share/apache2/icons/pie4.png
apache2.2-common: /usr/share/apache2/icons/pie5.gif
apache2.2-common: /usr/share/apache2/icons/pie5.png
apache2.2-common: /usr/share/apache2/icons/pie6.gif
apache2.2-common: /usr/share/apache2/icons/pie6.png
apache2.2-common: /usr/share/apache2/icons/pie7.gif
apache2.2-common: /usr/share/apache2/icons/pie7.png
apache2.2-common: /usr/share/apache2/icons/pie8.gif
apache2.2-common: /usr/share/apache2/icons/pie8.png
apache2.2-common: /usr/share/apache2/icons/portal.gif
apache2.2-common: /usr/share/apache2/icons/portal.png
apache2.2-common: /usr/share/apache2/icons/ps.gif
apache2.2-common: /usr/share/apache2/icons/ps.png
apache2.2-common: /usr/share/apache2/icons/quill.gif
apache2.2-common: /usr/share/apache2/icons/quill.png
apache2.2-common: /usr/share/apache2/icons/right.gif
apache2.2-common: /usr/share/apache2/icons/right.png
apache2.2-common: /usr/share/apache2/icons/screw1.gif
apache2.2-common: /usr/share/apache2/icons/screw1.png
apache2.2-common: /usr/share/apache2/icons/screw2.gif
apache2.2-common: /usr/share/apache2/icons/screw2.png
apache2.2-common: /usr/share/apache2/icons/script.gif
apache2.2-common: /usr/share/apache2/icons/script.png
apache2.2-common: /usr/share/apache2/icons/small
apache2.2-common: /usr/share/apache2/icons/small/back.gif
apache2.2-common: /usr/share/apache2/icons/small/back.png
apache2.2-common: /usr/share/apache2/icons/small/binary.gif
apache2.2-common: /usr/share/apache2/icons/small/binary.png
apache2.2-common: /usr/share/apache2/icons/small/binhex.gif
apache2.2-common: /usr/share/apache2/icons/small/binhex.png
apache2.2-common: /usr/share/apache2/icons/small/blank.gif
apache2.2-common: /usr/share/apache2/icons/small/blank.png
apache2.2-common: /usr/share/apache2/icons/small/broken.gif
apache2.2-common: /usr/share/apache2/icons/small/broken.png
apache2.2-common: /usr/share/apache2/icons/small/burst.gif
apache2.2-common: /usr/share/apache2/icons/small/burst.png
apache2.2-common: /usr/share/apache2/icons/small/comp1.gif
apache2.2-common: /usr/share/apache2/icons/small/comp1.png
apache2.2-common: /usr/share/apache2/icons/small/comp2.gif
apache2.2-common: /usr/share/apache2/icons/small/comp2.png
apache2.2-common: /usr/share/apache2/icons/small/compressed.gif
apache2.2-common: /usr/share/apache2/icons/small/compressed.png
apache2.2-common: /usr/share/apache2/icons/small/continued.gif
apache2.2-common: /usr/share/apache2/icons/small/continued.png
apache2.2-common: /usr/share/apache2/icons/small/dir.gif
apache2.2-common: /usr/share/apache2/icons/small/dir.png
apache2.2-common: /usr/share/apache2/icons/small/dir2.gif
apache2.2-common: /usr/share/apache2/icons/small/dir2.png
apache2.2-common: /usr/share/apache2/icons/small/doc.gif
apache2.2-common: /usr/share/apache2/icons/small/doc.png
apache2.2-common: /usr/share/apache2/icons/small/forward.gif
apache2.2-common: /usr/share/apache2/icons/small/forward.png
apache2.2-common: /usr/share/apache2/icons/small/generic.gif
apache2.2-common: /usr/share/apache2/icons/small/generic.png
apache2.2-common: /usr/share/apache2/icons/small/generic2.gif
apache2.2-common: /usr/share/apache2/icons/small/generic2.png
apache2.2-common: /usr/share/apache2/icons/small/generic3.gif
apache2.2-common: /usr/share/apache2/icons/small/generic3.png
apache2.2-common: /usr/share/apache2/icons/small/image.gif
apache2.2-common: /usr/share/apache2/icons/small/image.png
apache2.2-common: /usr/share/apache2/icons/small/image2.gif
apache2.2-common: /usr/share/apache2/icons/small/image2.png
apache2.2-common: /usr/share/apache2/icons/small/index.gif
apache2.2-common: /usr/share/apache2/icons/small/index.png
apache2.2-common: /usr/share/apache2/icons/small/key.gif
apache2.2-common: /usr/share/apache2/icons/small/key.png
apache2.2-common: /usr/share/apache2/icons/small/movie.gif
apache2.2-common: /usr/share/apache2/icons/small/movie.png
apache2.2-common: /usr/share/apache2/icons/small/patch.gif
apache2.2-common: /usr/share/apache2/icons/small/patch.png
apache2.2-common: /usr/share/apache2/icons/small/ps.gif
apache2.2-common: /usr/share/apache2/icons/small/ps.png
apache2.2-common: /usr/share/apache2/icons/small/rainbow.gif
apache2.2-common: /usr/share/apache2/icons/small/rainbow.png
apache2.2-common: /usr/share/apache2/icons/small/sound.gif
apache2.2-common: /usr/share/apache2/icons/small/sound.png
apache2.2-common: /usr/share/apache2/icons/small/sound2.gif
apache2.2-common: /usr/share/apache2/icons/small/sound2.png
apache2.2-common: /usr/share/apache2/icons/small/tar.gif
apache2.2-common: /usr/share/apache2/icons/small/tar.png
apache2.2-common: /usr/share/apache2/icons/small/text.gif
apache2.2-common: /usr/share/apache2/icons/small/text.png
apache2.2-common: /usr/share/apache2/icons/small/transfer.gif
apache2.2-common: /usr/share/apache2/icons/small/transfer.png
apache2.2-common: /usr/share/apache2/icons/small/unknown.gif
apache2.2-common: /usr/share/apache2/icons/small/unknown.png
apache2.2-common: /usr/share/apache2/icons/small/uu.gif
apache2.2-common: /usr/share/apache2/icons/small/uu.png
apache2.2-common: /usr/share/apache2/icons/sound1.gif
apache2.2-common: /usr/share/apache2/icons/sound1.png
apache2.2-common: /usr/share/apache2/icons/sound2.gif
apache2.2-common: /usr/share/apache2/icons/sound2.png
apache2.2-common: /usr/share/apache2/icons/sphere1.gif
apache2.2-common: /usr/share/apache2/icons/sphere1.png
apache2.2-common: /usr/share/apache2/icons/sphere2.gif
apache2.2-common: /usr/share/apache2/icons/sphere2.png
apache2.2-common: /usr/share/apache2/icons/tar.gif
apache2.2-common: /usr/share/apache2/icons/tar.png
apache2.2-common: /usr/share/apache2/icons/tex.gif
apache2.2-common: /usr/share/apache2/icons/tex.png
apache2.2-common: /usr/share/apache2/icons/text.gif
apache2.2-common: /usr/share/apache2/icons/text.png
apache2.2-common: /usr/share/apache2/icons/transfer.gif
apache2.2-common: /usr/share/apache2/icons/transfer.png
apache2.2-common: /usr/share/apache2/icons/unknown.gif
apache2.2-common: /usr/share/apache2/icons/unknown.png
apache2.2-common: /usr/share/apache2/icons/up.gif
apache2.2-common: /usr/share/apache2/icons/up.png
apache2.2-common: /usr/share/apache2/icons/uu.gif
apache2.2-common: /usr/share/apache2/icons/uu.png
apache2.2-common: /usr/share/apache2/icons/uuencoded.gif
apache2.2-common: /usr/share/apache2/icons/uuencoded.png
apache2.2-common: /usr/share/apache2/icons/world1.gif
apache2.2-common: /usr/share/apache2/icons/world1.png
apache2.2-common: /usr/share/apache2/icons/world2.gif
apache2.2-common: /usr/share/apache2/icons/world2.png
apache2.2-common: /usr/share/apache2/icons/odf6odb-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6odc-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6odf-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6odg-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6odi-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6odm-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6odp-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6ods-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6odt-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6otc-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6otf-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6otg-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6oth-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6oti-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6otp-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6ots-20x22.png
apache2.2-common: /usr/share/apache2/icons/odf6ott-20x22.png
apache2.2-common: /usr/share/apache2/error
apache2.2-common: /usr/share/apache2/error/HTTP_BAD_GATEWAY.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_BAD_REQUEST.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_FORBIDDEN.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_GONE.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_INTERNAL_SERVER_ERROR.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_LENGTH_REQUIRED.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_METHOD_NOT_ALLOWED.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_NOT_FOUND.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_NOT_IMPLEMENTED.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_PRECONDITION_FAILED.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_REQUEST_TIME_OUT.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_REQUEST_URI_TOO_LARGE.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_SERVICE_UNAVAILABLE.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_UNAUTHORIZED.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
apache2.2-common: /usr/share/apache2/error/HTTP_VARIANT_ALSO_VARIES.html.var
apache2.2-common: /usr/share/apache2/error/README
apache2.2-common: /usr/share/apache2/error/contact.html.var
apache2.2-common: /usr/share/apache2/error/include
apache2.2-common: /usr/share/apache2/error/include/bottom.html
apache2.2-common: /usr/share/apache2/error/include/spacer.html
apache2.2-common: /usr/share/apache2/error/include/top.html
apache2.2-common: /usr/share/bug/apache2.2-common
apache2.2-common: /usr/share/bug/apache2.2-common/script
apache2.2-common: /usr/share/bug/apache2.2-common/control
apache2.2-common: /usr/share/lintian/overrides/apache2.2-common
apache2.2-common: /usr/share/doc/apache2.2-common
apache2.2-common: /usr/share/doc/apache2.2-common/examples
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-autoindex.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-dav.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-default.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-info.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-ssl.conf.gz
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-manual.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-mpm.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-multilang-errordoc.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-userdir.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-vhosts.conf
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-languages.conf.gz
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/magic.gz
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/mime.types.gz
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2/apache2.conf.gz
apache2.2-common: /usr/share/doc/apache2.2-common/examples/setup-instance
apache2.2-common: /usr/share/doc/apache2.2-common/examples/secondary-init-script
apache2.2-common: /usr/share/doc/apache2.2-common/examples/apache2.monit
apache2.2-common: /usr/share/doc/apache2.2-common/README.backtrace
apache2.2-common: /usr/share/doc/apache2.2-common/README.multiple-instances
apache2.2-common: /usr/share/doc/apache2.2-common/NEWS.Debian.gz
apache2.2-common: /usr/share/doc/apache2.2-common/copyright
apache2.2-common: /usr/share/doc/apache2.2-common/changelog.gz
apache2.2-common: /usr/share/doc/apache2.2-common/README.mpm-itk.gz
apache2.2-common: /usr/share/doc/apache2.2-common/changelog.mpm-itk.gz
apache2.2-common: /usr/share/doc/apache2.2-common/changelog.mpm-itk.Debian.gz
apache2.2-common: /usr/share/doc/apache2.2-common/README.Debian.gz
apache2.2-common: /usr/share/doc/apache2.2-common/changelog.Debian.gz
apache2.2-common: /usr/share/man/man8/apache2.8.gz
apache2.2-common: /usr/share/man/man8/apache2ctl.8.gz
apache2.2-common: /usr/sbin/apache2ctl
apache2.2-common: /var/cache/apache2
apache2.2-common: /var/cache/apache2/mod_disk_cache
apache2.2-common: /var/log/apache2
apparmor: /etc/apparmor.d/abstractions/apache2-common
apache2-utils: /usr/share/doc/apache2-utils
apache2-utils: /usr/share/doc/apache2-utils/copyright
apache2-utils: /usr/share/doc/apache2-utils/changelog.gz
apache2-utils: /usr/share/doc/apache2-utils/changelog.Debian.gz
apache2.2-bin: /usr/lib/apache2
apache2.2-bin: /usr/lib/apache2/mpm-worker
apache2.2-bin: /usr/lib/apache2/mpm-worker/apache2
apache2.2-bin: /usr/lib/apache2/mpm-prefork
apache2.2-bin: /usr/lib/apache2/mpm-prefork/apache2
apache2.2-bin: /usr/lib/apache2/mpm-event
apache2.2-bin: /usr/lib/apache2/mpm-event/apache2
apache2.2-bin: /usr/lib/apache2/mpm-itk
apache2.2-bin: /usr/lib/apache2/mpm-itk/apache2
apache2.2-bin: /usr/lib/apache2/modules
apache2.2-bin: /usr/lib/apache2/modules/mod_authn_file.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authn_dbm.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authn_anon.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authn_dbd.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authn_default.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authn_alias.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authz_host.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authz_groupfile.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authz_user.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authz_dbm.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authz_owner.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authnz_ldap.so
apache2.2-bin: /usr/lib/apache2/modules/mod_authz_default.so
apache2.2-bin: /usr/lib/apache2/modules/mod_auth_basic.so
apache2.2-bin: /usr/lib/apache2/modules/mod_auth_digest.so
apache2.2-bin: /usr/lib/apache2/modules/mod_file_cache.so
apache2.2-bin: /usr/lib/apache2/modules/mod_cache.so
apache2.2-bin: /usr/lib/apache2/modules/mod_disk_cache.so
apache2.2-bin: /usr/lib/apache2/modules/mod_mem_cache.so
apache2.2-bin: /usr/lib/apache2/modules/mod_dbd.so
apache2.2-bin: /usr/lib/apache2/modules/mod_dumpio.so
apache2.2-bin: /usr/lib/apache2/modules/mod_reqtimeout.so
apache2.2-bin: /usr/lib/apache2/modules/mod_ext_filter.so
apache2.2-bin: /usr/lib/apache2/modules/mod_include.so
apache2.2-bin: /usr/lib/apache2/modules/mod_filter.so
apache2.2-bin: /usr/lib/apache2/modules/mod_substitute.so
apache2.2-bin: /usr/lib/apache2/modules/mod_charset_lite.so
apache2.2-bin: /usr/lib/apache2/modules/mod_deflate.so
apache2.2-bin: /usr/lib/apache2/modules/mod_ldap.so
apache2.2-bin: /usr/lib/apache2/modules/mod_log_forensic.so
apache2.2-bin: /usr/lib/apache2/modules/mod_env.so
apache2.2-bin: /usr/lib/apache2/modules/mod_mime_magic.so
apache2.2-bin: /usr/lib/apache2/modules/mod_cern_meta.so
apache2.2-bin: /usr/lib/apache2/modules/mod_expires.so
apache2.2-bin: /usr/lib/apache2/modules/mod_headers.so
apache2.2-bin: /usr/lib/apache2/modules/mod_ident.so
apache2.2-bin: /usr/lib/apache2/modules/mod_usertrack.so
apache2.2-bin: /usr/lib/apache2/modules/mod_unique_id.so
apache2.2-bin: /usr/lib/apache2/modules/mod_setenvif.so
apache2.2-bin: /usr/lib/apache2/modules/mod_version.so
apache2.2-bin: /usr/lib/apache2/modules/mod_proxy.so
apache2.2-bin: /usr/lib/apache2/modules/mod_proxy_connect.so
apache2.2-bin: /usr/lib/apache2/modules/mod_proxy_ftp.so
apache2.2-bin: /usr/lib/apache2/modules/mod_proxy_http.so
apache2.2-bin: /usr/lib/apache2/modules/mod_proxy_scgi.so
apache2.2-bin: /usr/lib/apache2/modules/mod_proxy_ajp.so
apache2.2-bin: /usr/lib/apache2/modules/mod_proxy_balancer.so
apache2.2-bin: /usr/lib/apache2/modules/mod_ssl.so
apache2.2-bin: /usr/lib/apache2/modules/mod_mime.so
apache2.2-bin: /usr/lib/apache2/modules/mod_dav.so
apache2.2-bin: /usr/lib/apache2/modules/mod_status.so
apache2.2-bin: /usr/lib/apache2/modules/mod_autoindex.so
apache2.2-bin: /usr/lib/apache2/modules/mod_asis.so
apache2.2-bin: /usr/lib/apache2/modules/mod_info.so
apache2.2-bin: /usr/lib/apache2/modules/mod_suexec.so
apache2.2-bin: /usr/lib/apache2/modules/mod_cgid.so
apache2.2-bin: /usr/lib/apache2/modules/mod_cgi.so
apache2.2-bin: /usr/lib/apache2/modules/mod_dav_fs.so
apache2.2-bin: /usr/lib/apache2/modules/mod_dav_lock.so
apache2.2-bin: /usr/lib/apache2/modules/mod_vhost_alias.so
apache2.2-bin: /usr/lib/apache2/modules/mod_negotiation.so
apache2.2-bin: /usr/lib/apache2/modules/mod_dir.so
apache2.2-bin: /usr/lib/apache2/modules/mod_imagemap.so
apache2.2-bin: /usr/lib/apache2/modules/mod_actions.so
apache2.2-bin: /usr/lib/apache2/modules/mod_speling.so
apache2.2-bin: /usr/lib/apache2/modules/mod_userdir.so
apache2.2-bin: /usr/lib/apache2/modules/mod_alias.so
apache2.2-bin: /usr/lib/apache2/modules/mod_rewrite.so
apache2.2-bin: /usr/lib/apache2/modules/httpd.exp
apache2.2-bin: /usr/share/doc/apache2.2-bin
apache2.2-bin: /usr/share/doc/apache2.2-bin/README.backtrace
apache2.2-bin: /usr/share/doc/apache2.2-bin/copyright
apache2.2-bin: /usr/share/doc/apache2.2-bin/changelog.gz
apache2.2-bin: /usr/share/doc/apache2.2-bin/changelog.Debian.gz
bash-completion: /etc/bash_completion.d/apache2ctl
apache2-mpm-prefork: /usr/lib/apache2
apache2-mpm-prefork: /usr/lib/apache2/mpm-prefork
apache2-mpm-prefork: /usr/share/lintian/overrides/apache2-mpm-prefork
apache2-mpm-prefork: /usr/share/bug/apache2-mpm-prefork
apache2-mpm-prefork: /usr/sbin/apache2
apache2-mpm-prefork: /usr/share/bug/apache2-mpm-prefork/script
apache2-mpm-prefork: /usr/share/doc/apache2-mpm-prefork

```

---

### Post by qwertyjjj on 2012-02-03
This has happened again.
I tried to restart xampp but it couldn't as apache was already installed.
So, how can I get rid of xampp and just install the latest apache2 and mysql and then get running that way?

---

### Post by Lars Noodén on 2012-02-03
First, shutdown everything that came with xampp.

```

/opt/lampp/lampp stop

```

Then look for a directory called [font=Courier New]/opt/lampp[/font].  When you find it, erase it. 

To install Apache2 the right way:

```

sudo apt-get install apache2

```

---

