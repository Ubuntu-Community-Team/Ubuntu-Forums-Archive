---
title: "Call to 'php5' caused command not found error."
date: 2010-01-06
forum: General Help
---

### Post by Silvernail on 2010-01-06
I have recently installed 9.10. Under 7.04 thru 9.04 I have a bash script and php script that I used to send announcements about club events.

When I tried it today, I get errors. Here us the command line script I use to call the php mail handling script.

```
#!/bin/bash
## member calling for Dave


main()
{
cat pdlist28 | ( \
     while read admin; \
     do check_link $admin; done \
     )

}

PHP_EXEC='php5 -r'

check_link()
{
    member_email=$1
    
    php5 -f mailsender.php "$member_email" "two";
}


main

```
I am getting this error:
> ./send.sh: line 20: php5: command not found
```
sudo apt-get install php5
``` tells me I have the latest version.

```
-rwxr-xr-x 1 dave dave    1117 2010-01-06 13:32 mailsender.php
``` exists.

```
apropos java
```produces results.
```
apropos bash
```produces results.
```
apropos php5
```produces nothing.


```
locate php5
``` produces this long list.
> dave@dave:~/tffrobot$ locate php5
/etc/php5
/etc/apache2/mods-available/php5.conf
/etc/apache2/mods-available/php5.load
/etc/apache2/mods-enabled/php5.conf
/etc/apache2/mods-enabled/php5.load
/etc/apparmor.d/abstractions/php5
/etc/cron.d/php5
/etc/php5/apache2
/etc/php5/conf.d
/etc/php5/apache2/conf.d
/etc/php5/apache2/php.ini
/etc/php5/conf.d/pdo.ini
/media/6cdedbb0-a45c-46e0-a472-78b0cfe562e7/etc/apparmor.d/abstractions/php5
/usr/lib/php5
/usr/lib/apache2/modules/libphp5.so
/usr/lib/php5/20060613+lfs
/usr/lib/php5/libexec
/usr/lib/php5/maxlifetime
/usr/lib/php5/20060613+lfs/pdo.so
/usr/share/php5
/usr/share/doc/libapache2-mod-php5
/usr/share/doc/php5
/usr/share/doc/php5-common
/usr/share/doc/php5-common/CODING_STANDARDS.gz
/usr/share/doc/php5-common/CREDITS
/usr/share/doc/php5-common/EXTENSIONS.gz
/usr/share/doc/php5-common/NEWS.Debian.gz
/usr/share/doc/php5-common/README.CVS-RULES.gz
/usr/share/doc/php5-common/README.Debian.gz
/usr/share/doc/php5-common/README.Debian.security
/usr/share/doc/php5-common/README.EXT_SKEL.gz
/usr/share/doc/php5-common/README.PHP4-TO-PHP5-THIN-CHANGES.gz
/usr/share/doc/php5-common/README.SELF-CONTAINED-EXTENSIONS.gz
/usr/share/doc/php5-common/README.Zeus.gz
/usr/share/doc/php5-common/TODO.Debian
/usr/share/doc/php5-common/TODO.gz
/usr/share/doc/php5-common/changelog.Debian.gz
/usr/share/doc/php5-common/changelog.gz
/usr/share/doc/php5-common/copyright
/usr/share/doc/php5-common/examples
/usr/share/doc/php5-common/test-results.txt.gz
/usr/share/doc/php5-common/examples/php.ini-dist
/usr/share/doc/php5-common/examples/php.ini-paranoid
/usr/share/doc/php5-common/examples/php.ini-recommended
/usr/share/lintian/overrides/libapache2-mod-php5
/usr/share/lintian/overrides/php5-common
/usr/share/php5/php.ini-dist
/usr/share/php5/php.ini-dist.cli
/var/cache/apt/archives/libapache2-mod-php5_5.2.10.dfsg.1-2ubuntu6.3_i386.deb
/var/cache/apt/archives/php5-common_5.2.10.dfsg.1-2ubuntu6.3_i386.deb
/var/cache/apt/archives/php5_5.2.10.dfsg.1-2ubuntu6.3_all.deb
/var/lib/php5
/var/lib/dpkg/info/libapache2-mod-php5.conffiles
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/libapache2-mod-php5.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5.prerm
/var/lib/dpkg/info/php5-common.conffiles
/var/lib/dpkg/info/php5-common.list
/var/lib/dpkg/info/php5-common.md5sums
/var/lib/dpkg/info/php5-common.postrm
/var/lib/dpkg/info/php5.list


What is missing?

---

### Post by Sef on 2010-01-06
Moved to General Help.

---

### Post by osstia on 2010-01-06
When looking for an executable in your path, try:
 
```
which php5
```
 
This will probably not return anything, just like your apropos command didn't. You should install php5-cli
 
```
sudo apt-get install php5-cli
```
 
That should install the tool you are looking for. Then both apropos and which should work.

---

### Post by slakkie on 2010-01-06
What the poster above me said: php5-cli

---

### Post by Silvernail on 2010-01-06
'php5-cli' did it.

Thanks guys
Dave

---

