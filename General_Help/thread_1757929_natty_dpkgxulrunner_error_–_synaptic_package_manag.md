---
title: "natty: dpkg/xulrunner error – synaptic package manager or update does not work"
date: 2011-05-14
forum: General Help
---

### Post by barnskybeat on 2011-05-14
Since upgrading to Natty I have a very annoying issue and since I am unable to resolve, please help me:

Whenever I start the synaptics package manager I get the following message:

An error occurred:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.


Once I run sudo dpkg --configure -a from the terminal this is what I get:

Setting up xulrunner-1.9.1 (1.9.1.18~hg20110309r27352+nobinonly-0ubuntu1~umd1) ...


No further progress the machine hangs indefinitely on this, need to kill terminal to exit. Even hours waiting does not show any progress.

Can please someone guide me step by step on how to revolve this issue?

Thanks

---

### Post by Cushie on 2011-05-14
>>[QUOTE=barnskybeat;10813277]Since upgrading to Natty I have a very annoying issue and since I am unable to resolve, please help me:

Setting up xulrunner-1.9.1 (1.9.1.18~hg20110309r27352+nobinonly-0ubuntu1~umd1) ...  <<


I have the same problem after a recent update, I get this hang-up after running 'apt-get' in terminal.
Hoping some suggestions can correct this.

---

### Post by barnskybeat on 2011-05-16
anyone out there who is able to help?

---

### Post by Michelle Rachel Ellert on 2011-05-16
Same (or similar) problem here. PM tries to resolve repository list and (sometimes) after an error message something like "Duplicate references" everything freezes with a constant HD seek (15 minutes +) requiring power down and rescue mode file system check.
I cleared the "/etc/apt/sources.list" text file as suggested but this seems to be a problem with a separate repository list maintained by PM not Debian. Also, early on as this was progressing the repository list was randomly dropping and duplicating entries.
Ubuntu 10.04 had a separate repository program and that may have been a better idea since I never had a problem with that. Otherwise no other problems with 11.04.
I'll check back later in case someone has found a fix and will post any I find though, for now I think I'll just avoid the Package Manager to avoid further damage.

---

### Post by amitdudhbade on 2011-05-27
I am getting same problem. Please suggest to resolve the issue.

---

### Post by Cushie on 2011-05-29
Well, one way or another I got rid of it.  I booted up in recovery mode, tried various options then eventually used 'Synaptic' and deleted all but the latest version of xulrunner.
Sorry to be not too precise but the problem has gone.
GL!

---

