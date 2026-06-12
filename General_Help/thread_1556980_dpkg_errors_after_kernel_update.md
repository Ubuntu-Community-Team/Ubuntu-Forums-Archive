---
title: "dpkg errors after kernel update?"
date: 2010-08-20
forum: General Help
---

### Post by s1mple_M4N on 2010-08-20
Hi all, just a small problem with lucid.

I have been quite happy with it since installation, but just tonight when I tried to uninstall qmmp (which I had been trialling as a music player) I came across this error.


roy@suzuki:~$ sudo apt-get remove qmmp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqmmp0 libqmmpui0 libbs2b3 libqmmp-misc
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  qmmp
0 upgraded, 0 newly installed, 1 to remove and 145 not upgraded.
After this operation, 1,487kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/available' near line 17605 package 'openoffice.org-core':
 `Conflicts' field, reference to `openoffice.org-officebean': error in version: epoch in version is not number
E: Sub-process /usr/bin/dpkg returned an error code (2)

I am dual-booting with Windoze XP and just this week notice 2 new ubuntu kernel lines in grub when my computer boots.

Not too sure what to do now - it seems I can't install or remove anything. Also, update manager does not work.

Has anyone else struck this??

Hoping for some assistance.

RoyJ

---

### Post by Rubi1200 on 2010-08-20
This link might help with diagnosing apt-get problems:

[http://www.linux.com/archive/feature/48910](http://www.linux.com/archive/feature/48910)

As far as the extra GRUB entries are concerned; quite normal.

Hope this helps.

---

### Post by s1mple_M4N on 2010-08-21
A very strange thing has happened - apparently today it has randomly repaired itself.

Thanks for the reply.

---

