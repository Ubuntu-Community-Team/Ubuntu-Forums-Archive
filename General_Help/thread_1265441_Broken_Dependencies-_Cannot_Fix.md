---
title: "Broken Dependencies- Cannot Fix"
date: 2009-09-13
forum: General Help
---

### Post by deafinmyleft on 2009-09-13
Hi all, thanks in advance for your help :)

When I try to install a program via apt-get or by opening the .deb file, I get a message saying my system has broken dependencies and to run 'sudo apt-get -f install'.

When I do this, this is the output:

#################################################################
luke@tux:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libnspr4-dev
The following NEW packages will be installed:
  libnspr4-dev
0 upgraded, 1 newly installed, 0 to remove and 55 not upgraded.
2 not fully installed or removed.
Need to get 0B/259kB of archives.
After this operation, 1450kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 331994 files and directories currently installed.)
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.5-0ubuntu0.8.04.1_i386.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/libnspr4-dev_4.7.5-0ubuntu0.8.04.1_i386.deb (--unpack):
 trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev
[/B]dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4-dev_4.7.5-0ubuntu0.8.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
######################################################################

Any ideas?

Thanks!

---

### Post by jerrrys on 2009-09-13
lots of ideas

[http://www.google.com/search?q=Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+(1)&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+(1)&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by falconindy on 2009-09-13
I had a similar problem about a week ago. apt-get wasn't able to fix the problem, but synaptic was. If you bring up `gksu synaptic`, click on 'status' on the left, and then select 'broken'.

---

### Post by nikgare on 2009-09-13
Try cleaning the cache out to force a reload and then run apt-get -f install again:
**sudo apt-get clean**

---

### Post by steveneddy on 2009-09-14
Posts 3 & 4 are much better solutions.

If apt can't or won't fix it, always go to Synaptic first.

---

