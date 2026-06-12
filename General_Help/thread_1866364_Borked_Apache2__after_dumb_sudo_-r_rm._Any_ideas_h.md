---
title: "Borked Apache2  after dumb sudo -r rm. Any ideas how to fix?"
date: 2011-10-21
forum: General Help
---

### Post by anandamide on 2011-10-21
Yes, this is all my own fault, but sometimes the temptation to write

```
sudo rm
```

is just too much.

My apache config has been broken a while (I don't seriously employ a webserver, but I sometimes like playing around to see what I can / can't do). Fed up of my borked configuration files remaining no matter what arguments I applied to an apt-get command, I finally just did > sudo rm -r /etc/apache2 in a fit of pique.

Of course that completely borked things.

I've tried a number of re-install methods, the most recent listed here:

[http://ubuntuforums.org/showthread.php?t=913605](http://ubuntuforums.org/showthread.php?t=913605)

But I still get the following error when trying to start apache:

```
Syntax error on line 160 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration
```

I previously tried the fix suggested here:

[http://www.thrull.com/corner/webserver/apache-module-mod-authz-groupfile/](http://www.thrull.com/corner/webserver/apache-module-mod-authz-groupfile/)

But to no avail.

Anybody got any idea what gives?

---

### Post by WorMzy on 2011-10-21
Have you tried purging and then reinstalling?

```
sudo apt-get purge apache2.2-common smb2www apache2-doc && sudo apt-get install apache2
```

---

### Post by anandamide on 2011-10-21
Bah, thought you might have been on to something there! Thanks v much for the reply, anyways.

Sadly the same error message. I got the following warning:

dpkg: warning: while removing libapache2-mod-php5, directory '/etc/php5/apache2' not empty so not removed

Then

```
Creating config file /etc/php5/apache2filter/php.ini with new version
Action 'configtest' failed.
The Apache error log may have more information.
Your apache2 configuration is broken, so we're not restarting it for you.
E: Could not open lock file /var/lib/dpkg/lock - open (13:Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

(Those last two errors have me stumped, I'm not running any other instances of apt-get, etc, and am definitely sudo-ing the command!).

---

### Post by WorMzy on 2011-10-21
Don't worry too much about those last two errors, they happen woefully frequently. If you're sure that you're not running any other apt-get commands, and don't have Synaptic Package Manager open, etc, then just delete the lock file:

```
sudo rm /var/lib/dpkg/lock
```

(be careful with that command, we don't want another accident ;) )

Try reinstalling libapache2-mod-auth-plain

```
sudo apt-get install --reinstall libapache2-mod-auth-plain
```

If that still doesn't help, post the output of:

```
ls -l /etc/apache2/mods-enabled
```

and

```
ls -l /etc/apache2/mods-available
```

---

### Post by anandamide on 2011-10-22
Thanks again for the reply - sorry I haven't got back to you sooner, I was playing about on the sly yesterday from work. 

Tried your first suggestion to no avail; here's the output you requested:

ls -l /etc/apache2/mods-enabled

```
total 0
lrwxrwxrwx 1 root root 26 2011-10-21 14:46 cgi.load -> ../mods-available/cgi.load
lrwxrwxrwx 1 root root 33 2011-10-21 15:21 php5filter.conf -> ../mods-available/php5filter.conf
lrwxrwxrwx 1 root root 33 2011-10-21 15:21 php5filter.load -> ../mods-available/php5filter.load
```

ls -l /etc/apache2/mods-available 

```
total 376
-rw-r--r-- 1 root root  332 2011-09-01 11:25 actions.conf
-rw-r--r-- 1 root root   66 2011-09-01 11:25 actions.load
-rw-r--r-- 1 root root  815 2011-09-01 11:25 alias.conf
-rw-r--r-- 1 root root   62 2011-09-01 11:25 alias.load
-rw-r--r-- 1 root root   60 2011-09-01 11:25 asis.load
-rw-r--r-- 1 root root   72 2011-09-01 11:25 auth_basic.load
-rw-r--r-- 1 root root   74 2011-09-01 11:25 auth_digest.load
-rw-r--r-- 1 root root   74 2011-09-01 11:25 authn_alias.load
-rw-r--r-- 1 root root   72 2011-09-01 11:25 authn_anon.load
-rw-r--r-- 1 root root   85 2011-09-01 11:25 authn_dbd.load
-rw-r--r-- 1 root root   70 2011-09-01 11:25 authn_dbm.load
-rw-r--r-- 1 root root   78 2011-09-01 11:25 authn_default.load
-rw-r--r-- 1 root root   72 2011-09-01 11:25 authn_file.load
-rw-r--r-- 1 root root   90 2011-09-01 11:25 authnz_ldap.load
-rw-r--r-- 1 root root   72 2010-03-06 13:40 auth_plain.load
-rw-r--r-- 1 root root   70 2011-09-01 11:25 authz_dbm.load
-rw-r--r-- 1 root root   78 2011-09-01 11:25 authz_default.load
-rw-r--r-- 1 root root   82 2011-09-01 11:25 authz_groupfile.load
-rw-r--r-- 1 root root   72 2011-09-01 11:25 authz_host.load
-rw-r--r-- 1 root root   74 2011-09-01 11:25 authz_owner.load
-rw-r--r-- 1 root root   72 2011-09-01 11:25 authz_user.load
-rw-r--r-- 1 root root 3265 2011-09-01 11:25 autoindex.conf
-rw-r--r-- 1 root root   70 2011-09-01 11:25 autoindex.load
-rw-r--r-- 1 root root   62 2011-09-01 11:25 cache.load
-rw-r--r-- 1 root root   70 2011-09-01 11:25 cern_meta.load
-rw-r--r-- 1 root root   69 2011-09-01 11:25 cgid.conf
-rw-r--r-- 1 root root   60 2011-09-01 11:25 cgid.load
-rw-r--r-- 1 root root   58 2011-09-01 11:25 cgi.load
-rw-r--r-- 1 root root   76 2011-09-01 11:25 charset_lite.load
-rw-r--r-- 1 root root   37 2011-09-01 11:25 dav_fs.conf
-rw-r--r-- 1 root root   79 2011-09-01 11:25 dav_fs.load
-rw-r--r-- 1 root root   58 2011-09-01 11:25 dav.load
-rw-r--r-- 1 root root   68 2011-09-01 11:25 dav_lock.load
-rw-r--r-- 1 root root   58 2011-09-01 11:25 dbd.load
-rw-r--r-- 1 root root  438 2011-09-01 11:25 deflate.conf
-rw-r--r-- 1 root root   66 2011-09-01 11:25 deflate.load
-rw-r--r-- 1 root root  122 2011-09-01 11:25 dir.conf
-rw-r--r-- 1 root root   58 2011-09-01 11:25 dir.load
-rw-r--r-- 1 root root  604 2011-09-01 11:25 disk_cache.conf
-rw-r--r-- 1 root root   89 2011-09-01 11:25 disk_cache.load
-rw-r--r-- 1 root root   64 2011-09-01 11:25 dump_io.load
-rw-r--r-- 1 root root   58 2011-09-01 11:25 env.load
-rw-r--r-- 1 root root   66 2011-09-01 11:25 expires.load
-rw-r--r-- 1 root root   72 2011-09-01 11:25 ext_filter.load
-rw-r--r-- 1 root root   89 2011-09-01 11:25 file_cache.load
-rw-r--r-- 1 root root   64 2011-09-01 11:25 filter.load
-rw-r--r-- 1 root root   66 2011-09-01 11:25 headers.load
-rw-r--r-- 1 root root   62 2011-09-01 11:25 ident.load
-rw-r--r-- 1 root root   68 2011-09-01 11:25 imagemap.load
-rw-r--r-- 1 root root   66 2011-09-01 11:25 include.load
-rw-r--r-- 1 root root  408 2011-09-01 11:25 info.conf
-rw-r--r-- 1 root root   60 2011-09-01 11:25 info.load
-rw-r--r-- 1 root root  176 2011-09-01 11:25 ldap.conf
-rw-r--r-- 1 root root   60 2011-09-01 11:25 ldap.load
-rw-r--r-- 1 root root   76 2011-09-01 11:25 log_forensic.load
-rw-r--r-- 1 root root  185 2011-09-01 11:25 mem_cache.conf
-rw-r--r-- 1 root root   87 2011-09-01 11:25 mem_cache.load
-rw-r--r-- 1 root root 7411 2011-09-01 11:25 mime.conf
-rw-r--r-- 1 root root   60 2011-09-01 11:25 mime.load
-rw-r--r-- 1 root root   81 2011-09-01 11:25 mime_magic.conf
-rw-r--r-- 1 root root   72 2011-09-01 11:25 mime_magic.load
-rw-r--r-- 1 root root  666 2011-09-01 11:25 negotiation.conf
-rw-r--r-- 1 root root   74 2011-09-01 11:25 negotiation.load
-rw-r--r-- 1 root root  127 2011-10-14 23:40 php5filter.conf
-rw-r--r-- 1 root root   65 2011-10-14 23:40 php5filter.load
-rw-r--r-- 1 root root   87 2011-09-01 11:25 proxy_ajp.load
-rw-r--r-- 1 root root  355 2011-09-01 11:25 proxy_balancer.conf
-rw-r--r-- 1 root root   97 2011-09-01 11:25 proxy_balancer.load
-rw-r--r-- 1 root root  803 2011-09-01 11:25 proxy.conf
-rw-r--r-- 1 root root   95 2011-09-01 11:25 proxy_connect.load
-rw-r--r-- 1 root root  141 2011-09-01 11:25 proxy_ftp.conf
-rw-r--r-- 1 root root   87 2011-09-01 11:25 proxy_ftp.load
-rw-r--r-- 1 root root   89 2011-09-01 11:25 proxy_http.load
-rw-r--r-- 1 root root   62 2011-09-01 11:25 proxy.load
-rw-r--r-- 1 root root   89 2011-09-01 11:25 proxy_scgi.load
-rw-r--r-- 1 root root  429 2011-09-01 11:25 reqtimeout.conf
-rw-r--r-- 1 root root   72 2011-09-01 11:25 reqtimeout.load
-rw-r--r-- 1 root root   66 2011-09-01 11:25 rewrite.load
-rw-r--r-- 1 root root 1211 2011-09-01 11:25 setenvif.conf
-rw-r--r-- 1 root root   68 2011-09-01 11:25 setenvif.load
-rw-r--r-- 1 root root   66 2011-09-01 11:25 speling.load
-rw-r--r-- 1 root root 2750 2011-09-01 11:25 ssl.conf
-rw-r--r-- 1 root root   58 2011-09-01 11:25 ssl.load
-rw-r--r-- 1 root root  753 2011-09-01 11:25 status.conf
-rw-r--r-- 1 root root   64 2011-09-01 11:25 status.load
-rw-r--r-- 1 root root   72 2011-09-01 11:25 substitute.load
-rw-r--r-- 1 root root   64 2011-09-01 11:25 suexec.load
-rw-r--r-- 1 root root   70 2011-09-01 11:25 unique_id.load
-rw-r--r-- 1 root root  604 2011-09-01 11:25 userdir.conf
-rw-r--r-- 1 root root   66 2011-09-01 11:25 userdir.load
-rw-r--r-- 1 root root   70 2011-09-01 11:25 usertrack.load
-rw-r--r-- 1 root root   66 2011-09-01 11:25 version.load
-rw-r--r-- 1 root root   74 2011-09-01 11:25 vhost_alias.load

```

---

### Post by anandamide on 2011-10-22
For completeness' sake, here is the output from the purge and re-install you originally suggested. I noticed some errors when I performed it yesterday but copy/pasting and scrolling was not an option on the java terminal I was using.

Anayway, here's the output. A few are trivial (?), such as smb2www not being installed, therefore not being removed. Others - your call.

```
$sudo apt-get purge apache2.2-common smb2www apache2-doc && sudo 
apt-get install apache2

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smb2www is not installed, so not removed
Package apache2-doc is not installed, so not removed
The following package was automatically installed and is no longer required:
  php5-cli
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork
The following packages will be REMOVED
  apache2-mpm-itk*
The following NEW packages will be installed
  apache2-mpm-prefork
0 upgraded, 1 newly installed, 1 to remove and 12 not upgraded.
Need to get 0B/2,386B of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: apache2-mpm-itk: dependency problems, but removing anyway as you requested:
 libapache2-mod-php5filter depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is not installed.
  Package apache2-mpm-itk is to be removed.
 apache2 depends on apache2-mpm-worker (= 2.2.16-1ubuntu3.3) | apache2-mpm-prefork (= 2.2.16-1ubuntu3.3) | apache2-mpm-event (= 2.2.16-1ubuntu3.3) | apache2-mpm-itk (= 2.2.16-1ubuntu3.3); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not installed.
  Package apache2-mpm-event is not installed.
  Package apache2-mpm-itk is to be removed.
(Reading database ... 242850 files and directories currently installed.)
Removing apache2-mpm-itk ...
 * Stopping web server apache2                                           [ OK ] 
Selecting previously deselected package apache2-mpm-prefork.
(Reading database ... 242847 files and directories currently installed.)
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.16-1ubuntu3.3_i386.deb) ...
Setting up apache2-mpm-prefork (2.2.16-1ubuntu3.3) ...
 * Starting web server apache2                                                  Syntax error on line 160 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
invoke-rc.d: initscript apache2, action "start" failed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
The following package was automatically installed and is no longer required:
  php5-cli
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

```

Cheers :-)

---

### Post by mikejonesey on 2011-10-22
try 
```
sudo apt-get install --reinstall -f apache2
```

---

### Post by anandamide on 2011-10-22
Alas - same ol' error.

---

### Post by WorMzy on 2011-10-22
The problem is that you're missing about a dozen or so symlinks from /etc/apache2/mods-enabled. I thought that would be the problem, but I'd have expected a purge+reinstall of the related packages to fix it.

You could just re-create these symlinks manually, but I couldn't tell you what the default modules are on Ubuntu. Try the following:

```
sudo dpkg-reconfigure apache2-common
```

Then restart apache:

```
sudo restart apache2
```

If that doesn't do it, then try symlinking these files from /etc/apache2/modules-available to /etc/apache2/modules-enabled

```
authz_host.load
mime.conf
mime.load
autoindex.conf
autoindex.load
negotiation.conf
negotiation.load
dir.conf
dir.load
userdir.conf
userdir.load
alias.conf
alias.load
rewrite.load
```

e.g.
```
sudo ln -s /etc/apache2/modules-available/{authz_host.load,mime.conf
mime.load,autoindex.conf,autoindex.load,negotiation.conf,negotiation.load,dir.conf,dir.load,userdir.conf,userdir.load,alias.conf,alias.load,rewrite.load} /etc/apache2/modules-enabled
```
(That's a one-liner that might work. I don't use bash any more, but I'm pretty sure the syntax is the same as zsh)

Then restart apache again.

They're what I have enabled on my server, but I don't use Ubuntu, and I stripped out everything I wasn't using anyway. In any case, it should give you a usable server. If you plan on using PHP, make sure that it's installed, and that php.conf/php.load are linked too. If a Ubu-user could give you a list of their enabled modules, that'd be better.

---

### Post by mikejonesey on 2011-10-22
if your problem is still;

> Action 'configtest' failed.
The Apache error log may have more information.
Your apache2 configuration is broken, so we're not restarting it for you.
E: Could not open lock file /var/lib/dpkg/lock - open (13:Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

ensure there are no other apt services by greping ps and sudo su temporarily to become root, and also check /var/lib/dpkg/ dir for existance...

---

### Post by anandamide on 2011-10-23
mikejonesey: Sorry, I should have been more clear. The random permissions problem was just a surprising error that apt-get splurged out at the time (no other instances were running); the original problem was - and remains - the following error:

```
Syntax error on line 160 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration
```

WorMzy: Thanks for all that - frustratingly, still have the same error after executing both commands (with modifications - apache2-common is apache2.2-common in the repositories, and it's mods_* not modules_* on Ubuntu boxes).

At least you've given me a pointer as to where the error might lie; I'll do some digging around and see if I can come up with anything. Thanks again for your time.

(As an aside, I didn't know about that brace syntax you used in the ln command; that will come in *very* useful in the future, so not all has been in vain!).

---

### Post by WorMzy on 2011-10-23
> pache2-common is apache2.2-common in the repositories, and it's mods_* not modules_* on Ubuntu boxes

Ah, right. I had those right in an earlier post, but I guess I forgot.

Just double-check that those modules now have symlinks in mods-enabled; that specific error should be solved by enabling authz_host (I checked on my server -- disabling that mod produces the error, although it's not fatal).

---

### Post by anandamide on 2011-10-23
Ahah! Spot on - the ln command had got scrambled. I've just linked the files line by line, and am back to the error I was getting before I issued the $sudo rm -r /etc/apache2 command.

Which progress. How I love Linux. At least I'm not being circled by sharks yet...

[http://xkcd.com/349/](http://xkcd.com/349/)

Thanks so much for the help, I really appreciate it.

---

### Post by mikejonesey on 2011-10-24
cool cool, for future ref;
```
find /etc/apache2 -type f -exec grep -i "Order" '{}' \;
```
should have pointed you to the problem line... :)

---

### Post by jimcjulsonjr on 2012-12-09
I created an account here just so I could post a HUGE thanks.  I spent 3 days tracking this issue down, and there were SO many posts on so many websites that were just so wrong.  

It amazes me that the gentleman that figured out the symbolic link issue did so in just a few commands, then gave a 1 line solution to fix it.  It's almost like all the people out there don't even read the original text in it's entirety.  

Anyhow, thanks so much for these posts, and for the follow-up.  I know this is a little old, but still, beyond helpful!

---

