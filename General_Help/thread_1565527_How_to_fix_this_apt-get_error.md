---
title: "How to fix this apt-get error?"
date: 2010-09-01
forum: General Help
---

### Post by tacomodo on 2010-09-01
I'm trying to install something new, but no matter what I try to install I get errors. Does anyone have any tips?

First I run for instance
> root@nagios:~# apt-get install nagios-plugins-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nagios-plugins-standard is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nagios-plugins-standard: Depends: radiusclient1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Ok, then I try:
> root@nagios:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  radiusclient1
The following NEW packages will be installed:
  radiusclient1
0 upgraded, 1 newly installed, 0 to remove and 82 not upgraded.
9 not fully installed or removed.
Need to get 0B/34.6kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 49193 files and directories currently installed.)
Unpacking radiusclient1 (from .../radiusclient1_0.3.2-11.1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/radiusclient1_0.3.2-11.1ubuntu1_i386.deb (--unpack):
 **trying to overwrite '/usr/sbin/radlogin'**, which is also in package libradiusclient-ng-dev 0:0.5.6-1
Errors were encountered while processing:
 /var/cache/apt/archives/radiusclient1_0.3.2-11.1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
So then I try to set 777 on the file it's trying to overwrite, but still no go
> root@nagios:~# ls /usr/sbin/radlogin -la
-rwxrwxrwx 1 root root 18088 2009-05-02 21:43 /usr/sbin/radlogin

/var/log/dpkg.log looks like this, only longer
> root@nagios:~# cat /var/log/dpkg.log
2010-09-01 08:04:03 startup archives unpack
2010-09-01 08:04:03 install radiusclient1 <none> 0.3.2-11.1ubuntu1
2010-09-01 08:04:03 status half-installed radiusclient1 0.3.2-11.1ubuntu1
2010-09-01 08:04:03 status not-installed radiusclient1 <none>
2010-09-01 08:14:08 startup archives unpack


I've also tried apt-get clean, remove --purge, update and a lot of others things...

---

### Post by inso_741 on 2010-09-01
try this:
```
cd /var/cache/apt/archives
sudo rm -rf *
sudo mkdir partial
```

---

### Post by tacomodo on 2010-09-01
Thanks, but still the same error 
> You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
nagios-plugins-standard: Depends: radiusclient1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 

---

### Post by sikander3786 on 2010-09-01
Did you try "Fix broken packages" in Synaptic?

Also

```

sudo dpkg --configure -a

```

And at last...

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)


[COLOR="Red"]**Edit:**[/COLOR] Just a thought. What happens if you download radiusclient1 from [here]("http://packages.ubuntu.com/search?keywords=radiusclient1&searchon=names&suite=lucid&section=all") and try to install it. Will it solve the dependency issue?

---

### Post by tacomodo on 2010-09-01
dpkg --configure -a
> root@nagios:/opt# dpkg --configure -a
dpkg: dependency problems prevent configuration of nagios-plugins-standard:
 nagios-plugins-standard depends on radiusclient1; however:
  Package radiusclient1 is not installed.
dpkg: error processing nagios-plugins-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios-plugins:
 nagios-plugins depends on nagios-plugins-standard; however:
  Package nagios-plugins-standard is not configured yet.
dpkg: error processing nagios-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up nagios-plugins-basic (1.4.13+git200906171200-1ubuntu3) ...

Creating config file /etc/nagios-plugins/config/apt.cfg with new version
cp: cannot create regular file `/etc/nagios-plugins/config/apt.cfg': No such file or directory
dpkg: error processing nagios-plugins-basic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nagios-plugins-standard
 nagios-plugins
 nagios-plugins-basic



Manual install of the package:
> root@nagios:/opt# dpkg -i radiusclient1_0.3.2-13_i386.deb 
dpkg: regarding radiusclient1_0.3.2-13_i386.deb containing radiusclient1:
 radiusclient1 conflicts with libradiusclient-ng-dev
  libradiusclient-ng-dev (version 0.5.6-1) is present and installed.
dpkg: error processing radiusclient1_0.3.2-13_i386.deb (--install):
 conflicting packages - not installing radiusclient1
Errors were encountered while processing:
 radiusclient1_0.3.2-13_i386.deb


---

### Post by inso_741 on 2010-09-01
take a look [here]("http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg249717.html")

---

### Post by tacomodo on 2010-09-01
Did dpkg -r on the three nagios plugin packages I was trying to install and it seems to be back to normal now.

---

### Post by dino99 on 2010-09-01
you might check the sources: only use packages from the same distro/release (open synaptic repo tab)

you can try to find, into synaptic, which package(s) to blame about partial upgrade (check broken package(s) there too)

---

