---
title: "Apache does not process PHP"
date: 2010-06-22
forum: General Help
---

### Post by peredur on 2010-06-22
It's a long story that I won't bore you with, but Apache2 on Ubuntu 10.04 no longer parses PHP files.  I've done a complete uninstall and reinstall of both Apache and PHP, but no joy.  In the Apache2 log, I get this message:

 /usr/lib/php5/20090626+lfs/xdebug.so: cannot open shared object file

I've done the obvious and checked that the library is there and it is.  It has permissions of 644 (rw-r--r--).

Does anyone know what I'm missing here?

Thanks


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by WorMzy on 2010-06-22
I know you said you've done a complete uninstall/reinstall of apache and php, but just to make sure: have you tried reinstalling apache2-mod-php5?

---

### Post by peredur on 2010-06-22
Hi,

Thanks for the reply.  I had reinstalled it (apache2-mod-php5), but I re-reinstalled it just to make sure.  No change.

:(

Cheers


Peter

---

### Post by peredur on 2010-06-22
Actually, apache2-mod-php5 doesn't appear to be installing correctly:

peter@peter-linux:~$ sudo dpkg -l libapache2-mod-php5
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libapache2-mod 5.3.2-1ubuntu4 server-side, HTML-embedded scripting languag
peter@peter-linux:~$ 

I have to say that doesn't mean a lot to me, but it doesn't look right.

Cheers

Peter

---

### Post by WorMzy on 2010-06-22
I agree, that doesn't look right. Did you purge it to begin with, or just remove it? If you just removed it, then try purging it and reinstalling with: ```
sudo apt-get remove --purge libapache2-mod-php5 && sudo apt-get install libapache2-mod-php5
```

---

### Post by Yarui on 2010-06-22
> **peredur said:**
> It's a long story that I won't bore you with, but Apache2 on Ubuntu 10.04 no longer parses PHP files.

I'm not sure if you are just talking about yourself or if you are assuming that it doesn't work on 10.04 in general.  If you are worried that 10.04 has screwed something up and it doesn't work at all anymore, though, I have good news for you.  Apache2 parses PHP just fine on my 10.04 machine, so this is definitely being caused by something else.

---

### Post by peredur on 2010-06-22
> **Yarui said:**
> I'm not sure if you are just talking about yourself or if you are assuming that it doesn't work on 10.04 in general.  If you are worried that 10.04 has screwed something up and it doesn't work at all anymore, though, I have good news for you.  Apache2 parses PHP just fine on my 10.04 machine, so this is definitely being caused by something else.

No.  Apologies.  I was just talking about myself.  It wasn't clear in my post, I agree.

And in fact it was working for me, earlier.

Cheers


Peter

---

### Post by peredur on 2010-06-22
> **WorMzy said:**
> I agree, that doesn't look right. Did you purge it to begin with, or just remove it? If you just removed it, then try purging it and reinstalling with: ```
sudo apt-get remove --purge libapache2-mod-php5 && sudo apt-get install libapache2-mod-php5
```

Still not installing properly, and still not parsing.  Here's the output:

```

peter@peter-linux:~$ sudo apt-get remove --purge libapache2-mod-php5 && sudo apt-get install libapache2-mod-php5
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  erlang-inets erlang-syntax-tools libsctp1 erlang-mnesia
  libcouchdb-glib-1.0-2 python-gtkspell python-couchdb python-avahi
  erlang-xmerl lksctp-tools erlang-crypto python-egenix-mxdatetime
  libdesktopcouch-glib-1.0-2 python-egenix-mxtools erlang-ssl
  erlang-runtime-tools erlang-base erlang-public-key python-indicate
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  libapache2-mod-php5* php5*
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 7,758kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 336374 files and directories currently installed.)
Removing php5 ...
Removing libapache2-mod-php5 ...
Module php5 disabled.
Run '/etc/init.d/apache2 restart' to activate new configuration!
Purging configuration files for libapache2-mod-php5 ...
dpkg: warning: while removing libapache2-mod-php5, directory '/etc/php5/apache2' not empty so not removed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  erlang-inets erlang-syntax-tools libsctp1 erlang-mnesia
  libcouchdb-glib-1.0-2 python-gtkspell python-couchdb python-avahi
  erlang-xmerl lksctp-tools erlang-crypto python-egenix-mxdatetime
  libdesktopcouch-glib-1.0-2 python-egenix-mxtools erlang-ssl
  erlang-runtime-tools erlang-base erlang-public-key python-indicate
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  libapache2-mod-php5
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/2,831kB of archives.
After this operation, 7,737kB of additional disk space will be used.
Selecting previously deselected package libapache2-mod-php5.
(Reading database ... 336373 files and directories currently installed.)
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.3.2-1ubuntu4.2_i386.deb) ...
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.2) ...

Creating config file /etc/php5/apache2/php.ini with new version
 * Reloading web server config apache2                                   [ OK ] 

peter@peter-linux:~$ sudo dpkg -l libapache2-mod-php5Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libapache2-mod 5.3.2-1ubuntu4 server-side, HTML-embedded scripting languag
peter@peter-linux:~$ 

```

Again, I confess that this doesn't mean a lot to me.

Cheers


Peter

---

### Post by Jeff250 on 2010-06-22
'dpkg -l libapache2-mod-php5' prints the same thing on my server where it works correctly.

It looks like the xdebug.so file is provided by the php5-xdebug package.  Try removing it and see if php works again.  If you need this package, then try reinstalling it.  If reinstalling breaks things again, you may need to do some additional troubleshooting to see why php5-xdebug is breaking things for you.

---

### Post by WorMzy on 2010-06-22
I just booted into Ubuntu, and I'm getting the same message when running dpkg -l libapache2-mod-php5, but my apache *is* parsing PHP.

So I guess that message is normal.

However, I don't have /usr/lib/php5/20090626+lfs/xdebug.so; I don't even have the folder "20090626+lfs", I do have one called "20090626", but there's no xdebug in there.

So I guess you're using another module, which is causing the errors. I did a google search on xdebug, and it seems it's a PHP debugger. So I looked in Synaptic, and sure enough, there's a php5-xdebug package. If you have that installed, then you could try reinstalling it, or removing it if that doesn't work.

EDIT: Guess I should search a little quicker. :P

---

### Post by peredur on 2010-06-22
> **WorMzy said:**
> I just booted into Ubuntu, and I'm getting the same message when running dpkg -l libapache2-mod-php5, but my apache *is* parsing PHP.

So I guess that message is normal.

However, I don't have /usr/lib/php5/20090626+lfs/xdebug.so; I don't even have the folder "20090626+lfs", I do have one called "20090626", but there's no xdebug in there.

So I guess you're using another module, which is causing the errors. I did a google search on xdebug, and it seems it's a PHP debugger. So I looked in Synaptic, and sure enough, there's a php5-xdebug package. If you have that installed, then you could try reinstalling it, or removing it if that doesn't work.

EDIT: Guess I should search a little quicker. :P

Nope.  'Fraid not.  Uninstalled it (and restarted Apache), but it still won't parse.  Anyway, it's past midnight here so I guess I'll have to leave it now until tomorrow.

Cheers


Peter

---

### Post by WorMzy on 2010-06-22
Did you do a remove --purge of that package? If not, try that, and if you're still getting the same xdebug error after that, then make sure that there's no file called xdebug.conf or xdebug.load in /etc/apache2/mods-enabled. If there is, remove them with sudo rm /etc/apache2/mods-enabled/xdebug.conf(or .load).

If that still doesn't fix it, then we're really running out of options. Doing a remove --purge on everything remotely related to apache2 and php5, then removing the related /etc directories seems a little over kill, but that should definitely work.

---

### Post by peredur on 2010-06-23
> **WorMzy said:**
> Did you do a remove --purge of that package? If not, try that, and if you're still getting the same xdebug error after that, then make sure that there's no file called xdebug.conf or xdebug.load in /etc/apache2/mods-enabled. If there is, remove them with sudo rm /etc/apache2/mods-enabled/xdebug.conf(or .load).

If that still doesn't fix it, then we're really running out of options. Doing a remove --purge on everything remotely related to apache2 and php5, then removing the related /etc directories seems a little over kill, but that should definitely work.

Thanks, WorMzy.  I suppose I should take comfort from the fact that this is not easy to better brains than mine...

I'll do what you suggest later on today (when I get back in front of the offending machine).  I did a "Complete removal" from Synaptic so I'm guessing it should have done just that.  Anyway I'll look for the files and remove them and try again.

If it doesn't work, I'll give the overkill a go.  I've nothing to lose, after all.

Cheers


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by peredur on 2010-06-23
> **WorMzy said:**
> Did you do a remove --purge of that package? If not, try that, and if you're still getting the same xdebug error after that, then make sure that there's no file called xdebug.conf or xdebug.load in /etc/apache2/mods-enabled. If there is, remove them with sudo rm /etc/apache2/mods-enabled/xdebug.conf(or .load).

If that still doesn't fix it, then we're really running out of options. Doing a remove --purge on everything remotely related to apache2 and php5, then removing the related /etc directories seems a little over kill, but that should definitely work.

But it doesn't.  Here's what I did.  First of all I made sure that everything to do with xdebug was gone:

```

peter@peter-linux:~$ sudo dpkg --purge php5-xdebug
[sudo] password for peter: 
dpkg: warning: ignoring request to remove php5-xdebug which isn't installed.
peter@peter-linux:~$ locate xdebug.conf
peter@peter-linux:~$
peter@peter-linux:~$ locate xdebug.load
peter@peter-linux:~$
peter@peter-linux:~$ cd /etc/apache2/mods-enabled
peter@peter-linux:/etc/apache2/mods-enabled$ ls
alias.conf	      authz_user.load  mime.conf	 reqtimeout.load
alias.load	      autoindex.conf   mime.load	 rewrite.load
auth_basic.load       autoindex.load   negotiation.conf  setenvif.conf
authn_file.load       cgi.load	       negotiation.load  setenvif.load
authz_default.load    dir.conf	       php5.conf	 status.conf
authz_groupfile.load  dir.load	       php5.load	 status.load
authz_host.load       env.load	       reqtimeout.conf

```

So no xdebug to be found anywhere and still not working.  Next, therefore I completely uninstalled (from Synaptic) everything to do with apache2 or php.  That is I marked everything *and their dependencies* for complete removal.  Then I get rid of everything related to apache and php from /etc:

```

peter@peter-linux:/etc/apache2/mods-enabled$ cd /etc
peter@peter-linux:/etc$ sudo rm -rf apache2
peter@peter-linux:/etc$ sudo rm -rf php5

```

Then I reinstalled the following:
*  apache2
*  apache2-docs
*  apache2-mpm-prefork
*  apache2-utils
*  apache2.2-bin
*  apache2.2-common
*  libapache2-mod-php5
*  php5-common

Tried again.  Apache works with HTML files, but will not parse PHP files.

(I confess at this point to being more than a little frustrated.  And yes, I did restart Apache: don't know why.  Just in case, I suppose.)

Cheers


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by WorMzy on 2010-06-23
Are you still getting the exact same error, or is it something different now?

Does the server just dispaly the contents of the PHP file, or does it just fail to load anything at all?

---

### Post by peredur on 2010-06-23
> **WorMzy said:**
> Are you still getting the exact same error, or is it something different now?

Does the server just dispaly the contents of the PHP file, or does it just fail to load anything at all?

Hi Sakura.  Many thanks for sticking with this one.

It's the same error in that Apache simply does not know what to do with the file.  Firefox says: You have chosen to open xxx.php which is a PHP script from [http://localhost](http://localhost).  What should Firefox do with this file? etc etc.

I'm not sure if that helps at all...

Cheers


Peter

---

### Post by WorMzy on 2010-06-23
Sakura's my PC. :P But you're welcome.

Unfortunately I can't think of anything else that could help. You said earlier that it was a long story, and you didn't want to post it all here, but is there anything you can think of that you might have done which could cause this? What was the last thing you did before the problem started?

---

### Post by peredur on 2010-06-23
> **WorMzy said:**
> Sakura's my PC. :P But you're welcome.

Unfortunately I can't think of anything else that could help. You said earlier that it was a long story, and you didn't want to post it all here, but is there anything you can think of that you might have done which could cause this? What was the last thing you did before the problem started?

And a beautifully named computer it is too.

Without being too boring, the background is that all was well with apache and php until I tried to install the Zend Server.  That originally caused the problem but then I purged Zemd Server and reinstalled libapache-mod-php5 and all was well.  However, I was persuaded to have another go with Zend Server.  The result was the same except that this time reinstalling mod-php doesn't cure the issue.  The people on the Zend Server forum got bored, apparently, before you because after a while I got no more help from there.  But hey!  It's free so I can't complain.  It may also be because I explained that I intend to change this box for another shortly.  Perhaps I should have kept quiet about that.

There you go.  Gone and done it again.  Haven't actually put hand to wallet, yet, either.

Cheers


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by WorMzy on 2010-06-23
I must admit, I'm not familiar with Zend at all, but I can't see why it would cause this sort of behaviour in another application; especially after a full purge and reinstallation of said program.

Is switching back to it an option, or did that suffer from similar/other problems?

This is really scraping the bottom of the barrel now, but if Zend doesn't work for whatever reason, then try following earlier steps and throwing an apt-get clean into the mix, just in case your installation .deb files are corrupted:
[LIST]
[*]Shutdown apache2
[*]Uninstall everything related to Apache2 and PHP5 again
[*]rm -fr /etc/apache2 and /etc/php5
[*]Run sudo apt-get clean
[*]Reinstall Apache2, php5 and libapache2-mod-php5
[*]Hope
[/LIST]

---

### Post by peredur on 2010-06-23
> **WorMzy said:**
> 
[LIST]
[*]Shutdown apache2
[*]Uninstall everything related to Apache2 and PHP5 again
[*]rm -fr /etc/apache2 and /etc/php5
[*]Run sudo apt-get clean
[*]Reinstall Apache2, php5 and libapache2-mod-php5
[*]Hope
[/LIST]

Once again the witching hour approaches this end.  I think I'll give this a go tomorrow, now.  I'll post tomorrow evening (GMT + 1) and let you know how I got on.

In the meantime, my grateful thanks for all your help.  I appreciate it.

Cheers


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by peredur on 2010-06-24
> **WorMzy said:**
> 
[LIST]
[*]Shutdown apache2
[*]Uninstall everything related to Apache2 and PHP5 again
[*]rm -fr /etc/apache2 and /etc/php5
[*]Run sudo apt-get clean
[*]Reinstall Apache2, php5 and libapache2-mod-php5
[*]Hope
[/LIST]


Nope.  Hope was in vain.  I guess it's wait for my new box or install LAMPP.  Probably the latter in the short term, in case I get a contract for PHP work in the meantime.

One thing's for sure, I won't be going anywhere near Zend again.

Cheers


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by peredur on 2010-06-25
Well, this is just the weirdest thing.  I uninstalled everything to do with apache and php and installed LAMPP (into /opt).  I started LAMPP and ran the security scripts and all that and then tried to run the usual:

```

<?php phpinfo(); ?>

```

to check that PHP was OK.

It wasn't.  I get exactly the same problem even using LAMPP.  I have to be missing something absolutely fundamental here.

Help??

Cheers


Peter
[http://www.peredur.net](http://www.peredur.net)

---

### Post by snyderpa on 2010-08-02
I was having the same problem. In my case the source was a condition in the configuration file at /etc/apache2/mods-available/php5.conf

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>


Since we are using libapache2-mod-php5 and not mod_php, I eliminated the condition and kept the AddType statements and restarted the apache server and that solved the problem. I am not sure what put the configuration file there -- I am using Zend Framework but also a whole lot of other carp.

---

### Post by peredur on 2010-08-03
> **snyderpa said:**
> I was having the same problem. In my case the source was a condition in the configuration file at /etc/apache2/mods-available/php5.conf



Hmm.  I don't have a file called /etc/apache2/mods-available/php5.conf.  Should I have?

Cheers


Peter

---

### Post by peredur on 2010-08-03
> **peredur said:**
> Hmm.  I don't have a file called /etc/apache2/mods-available/php5.conf.  Should I have?


I realised that I didn't have the files because I'd given up and uninstalled the module.  So I reinstalled it and tried again.  The contents of the php5.conf file after the installion were:

```

<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
	SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
	SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>

```

I had no luck with that, so I commented out the condition and restarted apache.  Still no luck.

Back to XAMPP on Windows for developing in PHP, then.  Annoying.

Cheers


Peter

---

### Post by peredur on 2010-09-25
As you'll see from the dates, I had this problem months ago and had given up on finding a solution.  Today, a propos something else entirely, I ran the following commands:

```

find /etc/apache2/ -type f -exec sudo chmod 644 {} \;
find /etc/apache2/ -type d -exec sudo chmod 755 {} \;
sudo chown -R root:root /etc/apache2

```

(For which I claim no credit.  They were from: [http://ubuntuforums.org/showthread.php?t=1288812](http://ubuntuforums.org/showthread.php?t=1288812).  I was adding an alias file and wanted to know what permissions to give it)

PHP is now parsed correctly, so I guess it was a permissions problem that the above has fixed.

Cheers


Peter

---

### Post by Burigufutsushide on 2010-11-05
I ran into this exact problem today and tried the various obvious things like removing and purging the packages and reinstalling. I also tried the permission suggestion by peredur without any effect. But then I accidently stumbled over the [community help pages]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205") which said > Be sure to clear your browser's cache before testing your site again. and just by doing this, things suddenly started working properly again. :)

Hope this can help someone.

---

