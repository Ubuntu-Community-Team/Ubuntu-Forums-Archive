---
title: "Cannot remove certains packages"
date: 2009-12-17
forum: General Help
---

### Post by AiRAVATA on 2009-12-17
Hello. I've (somehow) installed the cvs and menu packages, but something went wrong and every time I use aptitude or do an upgrade I recieve a message that cvs and menu cannot be removed.

If I type 

```
apt-get remove cvs menu
```

there is the following error message:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cvs menu
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 5,763kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 214580 files and directories currently installed.)
Removing cvs ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing cvs (--remove):
 subprocess installed pre-removal script returned error exit status 1
Removing menu ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing menu (--remove):
 subprocess installed pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cvs
 menu
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas on how tho get rid of this error?

---

### Post by jerrrys on 2009-12-17
sudo apt-get --purge remove cvs menu

maybe??

---

### Post by Darael on 2009-12-17
Hmm, I thought it had to be either "apt-get remove --purge <packages>" or use aptitude and do "aptitude purge <packages>"?

---

### Post by jerrrys on 2009-12-17
im on windows right now and can't verify that, so you could be right...

---

### Post by philinux on 2009-12-17
```
sudo apt-get purge packagename
```

will do. See man apt-get

> purge
purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).


---

### Post by AiRAVATA on 2009-12-17
```

sudo apt-get purge cvs menu

```

came out with the same error.

I've also tried to re-install the .deb's from packages.ubuntu.com in order to fix the install, and the same error pops out.

---

### Post by nibirumarduk on 2009-12-17
AiRAVATA, a piece of cake really ;) See this [http://ubuntuforums.org/showpost.php?p=8515102&postcount=2](http://ubuntuforums.org/showpost.php?p=8515102&postcount=2)

Good luck!

---

### Post by diesch on 2009-12-17
Looks like you have a wrong version of 
*install-info* ij your $PATH.

What does
```
 sudo which install-info
```and
```
 sudo install-info --version
```print?

---

### Post by nibirumarduk on 2009-12-17
@AiRAVATA and diesch

Forget the digging around. You will only get more confused. Trust me. Just go ahead with either Option 3 or Option 1 in [http://ubuntuforums.org/showpost.php?p=8515102&postcount=2](http://ubuntuforums.org/showpost.php?p=8515102&postcount=2)

Pretty much a no brainer. Can't see how things will still fail. But do get back to us should you still have issues with it.

Good luck!

---

### Post by diesch on 2009-12-17
I don't think that's a good idea.

If there really is a wrong version of install-info somewhere the same error will occur
again will again when (de)installing the next package containing info files.

Option 3 is particular bad as it just disables the whole script - which may lead to even more errors that are hard to track or even an unstable system.

---

### Post by nibirumarduk on 2009-12-17
> **diesch said:**
> I don't think that's a good idea.

If there really is a wrong version of install-info somewhere the same error will occur
again will again when (de)installing the next package containing info files.

Option 3 is particular bad as it just disables the whole script - which may lead to even more errors that are hard to track or even an unstable system.

The suggested solutions have worked for many and myself since 2002 when I started using Debian Sid/Experimental and then from 2007 onwards Ubuntu. In certain situations, Option 3 is the only option. I know of quite a few DDs i.e. Debian Developers using it quite often (i.e. a certain DD by the family name of Short comes to mind ;) ) In fact, that was the remedy recommended by a few DDs in #debian-devel (the Debian Developers' channel) which in 2002 was still hosted on freenode. If one has reservations about Option 3 then use Option 1 as it will suffice most of the time. 

Besides, newbies may not want to spend too much triaging but get on with it. Not saying that this should be the way but this is how most people are. Such buggy package scripts aren't a user's problem but one that speaks volumes of the QA process and of course the package maintainer himself/herself. I understand that package maintainers are only human and they do make mistakes but I'm not even asking for an OpenBSD like approach to auditing each and every package that is in their repos just a more robust QA process. Is that too much to ask for? Especially given the fact that Ubuntu is a distro targeted mainly at newcomers from both the Windows and Apple worlds, shouldn't the distro be more careful in this regard? Many a times, 1st impressions count. And depending on the situation such as this one, this 1st impression of the newcomer towards Ubuntu may be a very negative one. Forget not that just like a company cannot be a company without its customers and a democracy not a democracy without enfranchised voters, can a distro calls itself a distrothat listens not, cares not, disrespects or is without users a distro still?

I think we should respect AiRAVATA and his/her right to decide what he/she wants to do and go along with it. It is, after all, his/her system. AiRAVATA do you have the luxury of time? And even if you have such a luxury, would you not want to get on with doing your work? Or do you really want to continue troubleshooting what is a package maintainer's fault and job? Are you equipped with all of the necessary skills? The choice is yours. You have the choice.

Best of luck!

---

### Post by diesch on 2009-12-18
This solutions may be fine if you are working with unstable versions like Debian sid/experimental and problems are likely caused by buggy package scripts.
But even there I'll prefer to first find the real cause of an error before just fixing some symptoms.


But that's most likely not the case here. It's quite unlikely that a popular package like cvs has such an obvious bug.

The error message in typical for calling *GNU install-info* with *dpkg install-info* args, and as */var/lib/dpkg/info/cvs.prerm* is indeed calling *install-info with **dpkg install-info* args the error is likely to be caused by a version of  *GNU install-info* being installed by third party software.  Manually installed versions of TeXLive are often causing this problem.

---

### Post by AiRAVATA on 2010-01-06
Sorry for late reply, been afk for the holidays. Here is the info you requested:

```

usr@cpu:~$ sudo which install-info
/usr/local/bin/install-info

```
```

usr@cpu:~$ sudo install-info --version
install-info (GNU texinfo) 4.12

Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

```

Thanks for the help.

---

### Post by diesch on 2010-01-07
So most likely this */usr/local/bin/install-info* is causing your problem. Rename it to e.g. */usr/local/bin/ginstall-info* and see if that solves your problem.

If the package manager works now you is most likely fine to just leave the file renamed.

If you still get the same errors please tell what the two commands are printing after renaming */usr/local/bin/install-info*

---

### Post by AiRAVATA on 2010-01-07
> **diesch said:**
> So most likely this */usr/local/bin/install-info* is causing your problem. Rename it to e.g. */usr/local/bin/ginstall-info* and see if that solves your problem.


Worked like a charm. Thanks a lot!

---

