---
title: "RPM --rebuilddb fails"
date: 2012-09-09
forum: General Help
---

### Post by nem604 on 2012-09-09
Hi, I'm very new to Ubuntu and I've been having a problem with the rpmdb.

I was trying to install MySQL Server 5.5.27 and I read that I would have to use the RPM and use Alien to install it. I had an error because I already had a previous version of MySQL so I used Aptitude to delete MySQL. When I got around to using Alien again with the RPM I was having all sorts of errors including the one bellow. After lots of googling I managed to remove most of them, but I cant seem to get rid of the last few involving the rpmdb.

I've tried running rpm --rebuilddb as well as deleting the files in the rpm folder, but the folder contains no files to begin with. 

Can someone please help me?

> error: rpmdb: Thread/process 6853/140160051517184 failed: Thread died in Berkeley DB library
error: db5 error(-30973) from dbenv->failchk: DB_RUNRECOVERY: Fatal error, run database recovery
error: cannot open Packages index using db5 -  (-30973)


---

### Post by Zill on 2012-09-09
> **nem604 said:**
> ...I was trying to install MySQL Server 5.5.27 and I read that I would have to use the RPM and use Alien to install it...
I presume you do really *need* MySQL version 5.5.27?  I ask because the current version in Precise (the latest Ubuntu LTS) is 5.5.24 which is unlikely to be *much* different IMHO!

Trying to install RPMs into Ubuntu via Alien is sometimes *possible* but can give problems and so it is always better to find a DEB version IMO.

I see that Quantal (the next Ubuntu release) will include MySQL version 5.5.27 and so I suggest you could download this package and try installing it with GDebi.  If you are lucky then all the required dependencies will be present in your current release and so it should install OK.  However, if Gdebi cannot find the required dependencies then you should not proceed with installation at this stage.  You could then decide if it is worth upgrading to the Quantal Ubuntu beta release just to obtain MySQL 5.5.27.  Personally, I would not recommend this as servers should, IMO, always run on a stable release.

[LIST]
[*][Package: mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1)]("http://packages.ubuntu.com/precise/mysql-server-5.5")
[/LIST]

---

### Post by nem604 on 2012-09-09
Well I needed it for a class and my teacher specified to install MySQL server 5.5.27, but because it was giving me problems I stuck with 5.5.24. However what I'm trying to fix is the error I get whenever I execute any kind of rpm command. It won't let me rebuild the database so what else can I do?

---

### Post by jerome1232 on 2012-09-09
I'm not sure why your trying to muck about with rpm's on a Debian based distro, They do have .deb's here:

[http://dev.mysql.com/downloads/mysql/#downloads](http://dev.mysql.com/downloads/mysql/#downloads)


As previously stated, I doubt there's much difference between minor version changes.

---

### Post by nem604 on 2012-09-09
> **jerome1232 said:**
> I'm not sure why your trying to muck about with rpm's on a Debian based distro, They do have .deb's here:

[http://dev.mysql.com/downloads/mysql/#downloads](http://dev.mysql.com/downloads/mysql/#downloads)


As previously stated, I doubt there's much difference between minor version changes.

Thank you, I didn't see that. 

I'm currently trying to fix the issue where whenever I run a rpm command I get the errors mentioned previously.

---

### Post by Zill on 2012-09-10
> **nem604 said:**
> ...I'm currently trying to fix the issue where whenever I run a rpm command I get the errors mentioned previously.
Please note that "rpm" is ***not*** a native package format for Ubuntu.

Ubuntu is based on Debian, which uses the "deb" packaging format.  RPM refers to the packaging format created originally by Red Hat and is now used by other distros such as SUSE.

You will avoid problems if you stick to "deb" packages for Ubuntu, rather than trying to force packages in a different format into your (Debian based) Ubuntu system!

See [Linux package formats]("http://en.wikipedia.org/wiki/Linux_package_formats")

---

