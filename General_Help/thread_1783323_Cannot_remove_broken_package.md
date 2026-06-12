---
title: "Cannot remove broken package"
date: 2011-06-15
forum: General Help
---

### Post by ygoe on 2011-06-15
Hi,

I have installed a package that doesn't work on my system because some dependency is not met and I cannot resolve that without seriously breaking my system. Now I want to uninstall that package but it doesn't work. Every time, I get this message:

$ sudo dpkg --force-all -r libapache2-mod-geoip
(Reading database ... 188728 files and directories currently installed.)
Removing libapache2-mod-geoip ...
ERROR: Module geoip does not exist!
dpkg: error processing libapache2-mod-geoip (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-geoip

Synapic package manager is also not able to do anything with this broken package. How can I get rid of it now?

---

### Post by mistyautom on 2011-06-15
I would try using the following two commands:

sudo apt-get -f install

and then:

sudo apt-get remove libapache2-mod-geoip

---------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by ygoe on 2011-06-16
The error message remains the same in both commands. It finds the package, tries to remove it and then says that it cannot find it. Stupid APT!

---

### Post by John4582 on 2011-06-16
LonelyPixel

> **LonelyPixel said:**
> The error message remains the same in both commands. It finds the package, tries to remove it and then says that it cannot find it. Stupid APT!

I found these two commands that fixed my problems

**To list failed packed**; should list the failed/broken packages
I.E.
The following packages were automatically installed and are no longer required:
libnet-daemon-perl libhtml-template-perl libdbi-perl mysql-client-core-5.1 libdbd-mysql-perl mysql-server-5.1 mysql-client-5.1 mysql-common libplrpc-perl mysql-server-core-5.1 spawn-fcgi libmysqlclient16 libterm-readline-perl-perl php5-common


sudo apt-get --purge remove

and

**To automatically remove failed packages**; should list the failed/broken packages

I.E. 
The following packages will be REMOVED:
libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient16 libnet-daemon-perl libplrpc-perl libterm-readline-perl-perl mysql-client-5.1 mysql-client-core-5.1 mysql-common mysql-server-5.1 mysql-server-core-5.1 php5-common spawn-fcgi
0 upgraded, 0 newly installed, 14 to remove and 4 not upgraded.
After this operation, 56.0MB disk space will be freed.
Do you want to continue [Y/n]? 

sudo apt-get autoremove

Used at your own risk because I am a new-be with Linux but they worked for me.

---

### Post by ygoe on 2011-06-16
Nope, the first command did nothing else than my previous description. And the second command removed something else but still not geoip. It's stuck. Can I edit the package database by hand to remove all files and the package item? Possibly without corrupting the entire system?

If it helps, I could also restore single files from my backups. What files do I need to restore to get back the previous package database?

---

### Post by John4582 on 2011-06-16
LonelyPixel

> **LonelyPixel said:**
> Nope, the first command did nothing else than my previous description. And the second command removed something else but still not geoip. It's stuck. Can I edit the package database by hand to remove all files and the package item? Possibly without corrupting the entire system?

If it helps, I could also restore single files from my backups. What files do I need to restore to get back the previous package database?

What I did was to uninstall all package that I was having problems with.

What I started with was the Lighttpd web server and I wanted to remove it and use apache2. So I removed Lighttpd (so I thought). Then installed apache2 which failed. So I removed everything that I installed when I installed Lighttpd and removed apache2.

Using: sudo apt-get --purge remove <your package to remove)

Then: sudo apt-get --purge remove

Then: sudo apt-get autoremove

Then I started all over again installing apache2 and I didn't get any error or failed conditions.

I hope this helps.

Addition: Checking around I found the following:
> To also remove the debconf data, use the purge option when removing.  To  get rid of any configurations you may have made to apache, manually  remove the /etc/apache2 directory once the packages have been removed.

---

### Post by ygoe on 2011-06-16
Okay, I managed to resolve the situation. Since removing the half-installed package was absolutely impossible, the package needed to be fully installed to be handled again. Since it could not be installed because of dependency failures, I reinstalled the package like this:

sudo dpkg --force-depends -i package_name.deb

This installed the package with a warning but it completed. Then I could remove the package with the regular methods like sudo apt-get remove package_name. Now it's gone and there's no more warnings about a broken package system.

---

### Post by John4582 on 2011-06-16
**LonelyPixel**,

That's good to hear. Thanks for the update, I'll have to add that to my sudo commands for future reference. 

You should mark the thread as SOLVED so it easy for others to find solutions. 
 
John

---

### Post by dFlyer on 2011-06-16
Please mark this as solved

---

### Post by ygoe on 2011-06-17
Umm, where's the "solved" button? Can't find it.

---

### Post by wildmanne39 on 2011-06-17
> **LonelyPixel said:**
> Umm, where's the "solved" button? Can't find it.

Hi,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by hrishikesh1988 on 2011-06-17
hello 
try this 
sudo apt-get autoremove <pakagename>

---

