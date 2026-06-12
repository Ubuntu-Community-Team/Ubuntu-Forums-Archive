---
title: "libxml dependency problems"
date: 2006-03-01
forum: General Help
---

### Post by lynng on 2006-03-01
Quite some time ago, I followed a howto in the forums for installing checkgmail. I now use gmail-notify since it can easily be installed via apt rather than the much longer process for checkgmail. Somehow the xml stuff for checkgmail is now conflicting with other packages on the system. I've tried removing and reinstalling the 4 affected packages to no effect. Here's the output from apt:

```
lynng@eclipse:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-sax-expat-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

The "can't locate object method" line seems to be causing the problem.  For reference, [here's]("http://www.ubuntuforums.org/showthread.php?t=60418&highlight=howto+checkgmail") the checkgmail howto.  Anyone know how to fix?

---

### Post by Xian on 2006-03-01
What does this command offer:

$ sudo dpkg --configure -a
$ sudo dpkg --clear-avail

---

### Post by lynng on 2006-03-01
$ sudo dpkg --configure -a
```
lynng@eclipse:~$ sudo dpkg --configure -a
Password:
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-simple-perl
 libxml-sax-expat-perl
 libxml-libxml-perl

``` 
 $ sudo dpkg --clear-avail
does not return anything.

---

### Post by lynng on 2006-03-03
Well, does anyone know another support forum I might be able to ask for help?  Would my issue be more relevant to a support channel for apt or xml?  I  don't know where to go next.  I haven't been able to find anything in google that is specifically for libxml support.

---

### Post by sbassett on 2006-03-03
What does 
```
sudo apt-get -f install
```

return?

---

### Post by lynng on 2006-03-03
[quote=sbassett]What does 
```
sudo apt-get -f install
``` 
return?[/quote] 
The same output as before:
```
lynng@eclipse:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-sax-expat-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lynng on 2006-03-08
bump

---

### Post by Skye on 2006-03-13
I'm getting the same problem, only I'm using Dapper.  Same exact error, and same reason for installing (checkgmail.)

I posted a bug here: [https://launchpad.net/malone/bugs/34141]("https://launchpad.net/malone/bugs/34141"), but as yet it's had no response.

---

### Post by Obor on 2006-03-28
i'm also getting the same error, now I can't install some stuff that depends on those...
Anybody figured out how to fix it? I don't want to end up doing a reinstall as everything else is working fine. :confused:

---

### Post by lynng on 2006-04-19
Well, this isn't first issue I've encountered with Ubuntu (and linux in general - this isn't my first distro by a long shot) that absolutely no one in the forums has the expertise to answer.   No one with the expertise in #ubuntu, either.  It's not worth it to reinstall right now (and I thought one of the linux advantages was not having to do a clean instlall b/c of an issue like this :rolleyes:)

Doesn't really matter at the moment, since I rarely boot Ubuntu now anyway.  I even went so far as to change Grub to boot Windows by default.  I haven't take the step to remove it completely, however.  I still have hope.

When I boot my computer, I don't want to have to press ctrl-c to get past it hanging while trying to start networking (because of an apparently bad driver for the wireless card), I don't want to get errors about this libxml stuff every time I install something new, I want my graphics card to work fully (acceleration & tv out), I want to be able to upgrade Firefox without a page of instructions and a high risk factor, I want the fonts to look good from the start, I want my Bluetooth mouse to work properly (so I don't have to restart it every time it goes to sleep & the thumb buttons work), etc, etc, etc.  These are the issues I've been unable to resolve via google and following howtos in these forums.  The suggestions here simply haven't worked for my system. ](*,)

The waiting for things to work is just so very tiresome, especially when I can just reboot to Windows & have things work fine.  For now, I'm willing to sacrifice a little security to get those things, but then again I haven't had a Windows virus/trojan/worm/other in over three years.

Perhaps I should post this to a new thread :).  Each release of Ubuntu that I've tried (Hoary & Breezy) has gotten a little better.  Maybe Dapper will improve some of these things.  I honestly do enjoy working in Linux more than Windows, and it's fun to tinker.  I'm not afraid of the CLI or the man pages, and I do google and search the forums when I find an issue.  It's just these ongoing issues for which I can't find a solution that make it so frustrating to attempt to use Ubuntu as my primary OS.  I'm looking forward to installing Dapper when it's released.  Maybe I'll get to edit menu.lst in Ubuntu's favor again.

---

