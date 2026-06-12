---
title: "Upgrade Hardy -&gt; Lucid Broke Mediatomb"
date: 2011-01-09
forum: General Help
---

### Post by kaprikawn on 2011-01-09
Hi, I had Hardy Heron 64bit installed on my machine.  I recently upgraded the installation to Lucid and since then Mediatomb seems to have broken.  When I did a sudo apt-get upgrade I got the following:
```
user@myubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mediatomb-daemon (0.12.0~svn2018-6ubuntu2) ...
update-rc.d: /etc/init.d/mediatomb exists during rc.d purge (use -f to force)
dpkg: error processing mediatomb-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mediatomb:
 mediatomb depends on mediatomb-daemon (>= 0.12.0~svn2018-6ubuntu2); however:
  Package mediatomb-daemon is not configured yet.
dpkg: error processing mediatomb (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 mediatomb-daemon
 mediatomb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
So I did a sudo apt-get remove mediatomb with the intention of reinstalling it and that had similar results, it wouldn't let me remove it.  Can someone point me in the right direction, if only just to get rid of it because, call me a stickler, but I hate to see error messages during updates.

Many thanks in advance.

---

### Post by lithopsian on 2011-01-09
You can try```
sudo apt-get -f install
``` which often fixes dependency issues.  It often fixes them by removing packages so you might have to reinstall afterwards.

In this case dpkg looks like it is trying to do the right thing and failing for a very specific reason: /etc/init.d/mediatomb exists.  Delete it and go from there.  Maybe other problems will come up but nothing that can't be fixed.

---

