---
title: "Not able to install ZoneMinder"
date: 2011-03-14
forum: General Help
---

### Post by rensell on 2011-03-14
Hi all, I've decided to give ZoneMinder a try with a simple USB webcam that I've had laying around. I installed it in a VMware machine, but I could not get the webcam to "pass trough" to the virtual machine, so figured I would install ZoneMinder on the "regular" server...

I installed it, got annoyed, and autoremoved it. Now, I'm trying to reinstall it using ```
apt-get install zoneminder
``` and I'm getting a bunch of errors, 

```
Setting up zoneminder (1.24.2-2build3) ...
Starting ZoneMinder: DBI connect('database=zm;host=localhost','zmuser',...) failed: Unknown database 'zm' at /usr/share/perl5/ZoneMinder/Config.pm line 89
Can't call method "prepare_cached" on an undefined value at /usr/share/perl5/ZoneMinder/Config.pm line 91.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/share/perl5/ZoneMinder.pm line 33.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder.pm line 33.
Compilation failed in require at /usr/bin/zmpkg.pl line 45.
BEGIN failed--compilation aborted at /usr/bin/zmpkg.pl line 45.
failure

invoke-rc.d: initscript zoneminder, action "start" failed.
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

is the output on the screen, I've tried
```
sudo dpkg --configure -a
sudo apt-get install -f
```

and still get the errors. I'm somewhat new to Linux so any and all help is greatly appreciated.

Thanks so much,

-R

ps this is Ubuntu Server 10.04 - did update and upgrade tonight as well

---

### Post by lykeion on 2011-03-14
I can't make any sense of the error output, but did you try to remove the package completetly -- purge and clean -- before reinstalling it? (sudo omitted since you're on server)
```
apt-get purge zoneminder
apt-get clean
apt-get update
apt-get install zoneminder
```

Also the Zoneminder Wiki have install instructions for Ubuntu: [http://www.zoneminder.com/wiki/index.php/Ubuntu](http://www.zoneminder.com/wiki/index.php/Ubuntu)
And the Forums seems prestty active also: [http://www.zoneminder.com/forums/](http://www.zoneminder.com/forums/)

EDIT
It might have to do something with the database setup. Have you set a password for MySQL server?

---

### Post by rensell on 2011-03-14
```
apt-get clean
``` must have been the trick, I believe that ```
apt-get purge zoneminder
``` is run with ```
apt-get autoremove zoneminder
```, anyhow, I ran the commands you listed, got more errors on purge, ran clean update, install and success. It's working.... Thanks so much, now will add clean to troubleshooting steps.

Thanks again,

-r

---

### Post by lykeion on 2011-03-14
No problem, glad it worked out for you.

---

### Post by hwg5d6 on 2012-12-28
Works perfectly. I upgraded from 10 and I was getting very frustrated that the standard install was not working. Tanks.

---

