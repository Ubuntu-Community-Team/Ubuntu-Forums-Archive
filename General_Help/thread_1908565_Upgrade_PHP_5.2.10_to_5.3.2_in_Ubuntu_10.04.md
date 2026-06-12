---
title: "Upgrade PHP 5.2.10 to 5.3.2 in Ubuntu 10.04"
date: 2012-01-13
forum: General Help
---

### Post by Karys on 2012-01-13
Hello,
I have a problem upgrading my PHP in Ubuntu 10.04. I have the version  5.2.10. But I want to have php 5.3.2, Because I want to install the new  version of moodle that requires this version of php.
I made:
apt-get upgrade php5-cgi php5-cli
And it upgrade 38 packets, but I still have php 5.2.10.

With this command: apt-cache show libapache2-mod-php5 php5-cgi
I can see:

That all packets have 5.3 version. But,  this file dont have this version.
Package: libapache2-mod-php5
Status: install ok installed
Priority: optional
Section: httpd
Installed-Size: 5360
Source: php5
**Version: 5.2.10.dfsg.1-2ubuntu6.4**

I'm not sure if this is the problem.

Some of you have some suggestions? please.
Thanks a lot.

---

