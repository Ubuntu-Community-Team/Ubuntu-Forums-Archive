---
title: "Where Apache Located In Ubuntu"
date: 2010-02-21
forum: General Help
---

### Post by daniel50096230 on 2010-02-21
Anyone can guide me on how to find the Apache web server  on Ubuntu 9.04 and SmartPBX 1.2. I had found some guidelines from Internet to search for the Apache as following:

Apache config files are in /etc/apache no
Apache log files are in /var/log/apache
Apache libs are in /usr/lib/apache
Other files can be in /usr/share/apache, /var/lib/apache

However, I cannot found the said files.  What command should I type so that it will bring me to Apache folder?

Another question, currently I has a website which can be run locally. But how can I configure the website so that it could run on Internet.

---

### Post by spiderbatdad on 2010-02-21
apache is not installed by default...it is in synaptic package manager. The version is apache2.

so /etc/apache2...and so on.

---

### Post by daniel50096230 on 2010-02-21
I get what you means. But I can see localhost in the network tools, is it meas that Apache had been installed?

---

### Post by spiderbatdad on 2010-02-22
localhost is your machine and a number of services must run on it for the operating system to function.

to see what packages you have installed:
```
dpkg --list

or more specifically:

dpkg --list | grep apache2
```

---

