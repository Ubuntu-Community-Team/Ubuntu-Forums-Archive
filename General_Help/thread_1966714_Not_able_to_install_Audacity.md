---
title: "Not able to install Audacity"
date: 2012-04-27
forum: General Help
---

### Post by Mex5150 on 2012-04-27
Hi all, 

I'm wanting to install Audacity, but when I try (via Ubuntu Software Centre), I get:
**Failed to download package files**
Check your Internet connection.

My net connection is fine, when I try:
sudo apt-get install audacity
I get a warning that audacity-data audacity cannot be authenticated, if I continue anyway I get:```
Err http://archive.getdeb.net/ubuntu/ oneiric-getdeb/apps audacity-data all 1.3.14-1~getdeb1
  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)
Err http://archive.getdeb.net/ubuntu/ oneiric-getdeb/apps audacity i386 1.3.14-1~getdeb1
  Unable to connect to archive.getdeb.net:http:
Failed to fetch http://archive.getdeb.net/ubuntu/pool/apps/a/audacity/audacity-data_1.3.14-1~getdeb1_all.deb  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (113: No route to host)
Failed to fetch http://archive.getdeb.net/ubuntu/pool/apps/a/audacity/audacity_1.3.14-1~getdeb1_i386.deb  Unable to connect to archive.getdeb.net:http:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```I have tried "apt-get update --fix-missing" but it didn't help.

I'm running Ubuntu 11.10 if that is important.

Any ideas on how to fix this?

-Mex

---

### Post by Gremlinzzz on 2012-04-27
Are you using amd64 or i386?
REASON I'm looking at the package manager
[http://packages.ubuntu.com/oneiric/sound/audacity](http://packages.ubuntu.com/oneiric/sound/audacity)

why going try too add a mirror that works
ok
heres amd64  [http://packages.ubuntu.com/oneiric/amd64/audacity/download](http://packages.ubuntu.com/oneiric/amd64/audacity/download)



heres i386  [http://packages.ubuntu.com/oneiric/i386/audacity/download](http://packages.ubuntu.com/oneiric/i386/audacity/download)

read the top of the page 


If you are running Ubuntu, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website.

You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) oneiric main universe

Replacing ubuntu.mirror.cambrium.nl/ubuntu/ with the mirror in question.

---

### Post by Gremlinzzz on 2012-04-27
> **Gremlinzzz said:**
> Are you using amd64 or i386?
REASON I'm looking at the package manager
[http://packages.ubuntu.com/oneiric/sound/audacity](http://packages.ubuntu.com/oneiric/sound/audacity)

why going try too add a mirror that works
ok
heres amd64  [http://packages.ubuntu.com/oneiric/amd64/audacity/download](http://packages.ubuntu.com/oneiric/amd64/audacity/download)



heres i386  [http://packages.ubuntu.com/oneiric/i386/audacity/download](http://packages.ubuntu.com/oneiric/i386/audacity/download)

read the top of the page 


If you are running Ubuntu, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website.

You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) oneiric main universe

Replacing ubuntu.mirror.cambrium.nl/ubuntu/ with the mirror in question.

if you install the debs i see two packages

[http://packages.ubuntu.com/oneiric/sound/](http://packages.ubuntu.com/oneiric/sound/)

---

### Post by techsupport on 2012-04-27
> **Mex5150 said:**
> 

Any ideas on how to fix this?

-Mex

Uninstall the GebDeb PPA repository and install it from the Ubuntu repository. Works for me.  I avoid installing GebDeb if at all possible. There are better ways to install everything that is there. 

Try:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by Mex5150 on 2012-04-27
> **techsupport said:**
> Uninstall the GebDeb PPA repository and install it from the Ubuntu repository. Works for me.  I avoid installing GebDeb if at all possible. There are better ways to install everything that is there. 

Try:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)Right on the money, it was the GetDeb PPA that was breaking everything.

Thank you **both** for your help.

I can get on with some editing now :^>

-Mex

---

