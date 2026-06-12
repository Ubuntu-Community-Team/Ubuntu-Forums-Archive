---
title: "Cannot remove gforge-db-postgresql"
date: 2006-01-24
forum: General Help
---

### Post by bhogg on 2006-01-24
Hi all,

I seem to have run into a unique problem... after attempting unsuccessfully to install gforge (the top-level package uses apache and exim whereas I'd like apache2 and postfix), I'm attempting to remove the packages.  I used debfoster to get rid of most of the packages and their dependencies but cannot remove gforge-db-postgresql.  I receive the following error:

```
$ sudo apt-get remove gforge-db-postgresql
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gforge-db-postgresql
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 770kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88231 files and directories currently installed.)
Removing gforge-db-postgresql ...
cp: cannot stat `/etc/postgresql/pg_hba.conf': No such file or directory
dpkg: error processing gforge-db-postgresql (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gforge-db-postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have not deleted that file nor viewed it previously.  Perhaps one of the other packages I removed beforehand deleted it.  The /etc/postgresql folder doesn't even exist.

apt-get install doesn't do the trick either, stating that the package is already up to date.  Though I'd rather not install the package again just to immediately remove it, especially if it installs it's dependencies along with it.

Any ideas?

Also, if someone has successfully setup gforge using apache2/postfix on ubuntu 5.10 I'd love to hear about it.

Thanks,
Brian

---

### Post by mbria on 2006-02-13
I fall in the same issue... apache2, postfix and so on. :-(

Please, let us know if you or somebody find a solution. 
Gforge is exactly the tool I need for a new project I like to start.

Thanks a lot in advance,

marc.

---

### Post by welterde on 2006-04-18
I had the same problem. the problem is, the packages were made for debian not for ubuntu, so the only way is installation from scratch or using the VMWare-Image(in the free Player-version of it).
For sure the right, for an single project its over-dimensiond imho.
For an single project [trac]("http://projects.edgewall.com/trac/"), ist better.

---

