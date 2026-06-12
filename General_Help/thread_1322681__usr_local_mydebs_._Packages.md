---
title: "_usr_local_mydebs_._Packages"
date: 2009-11-11
forum: General Help
---

### Post by oldmankit on 2009-11-11
Hmmmm.  I can't find anything on the net that seems close enough to this problem.  On trying to open the gnone package manager, I get the following error:

> Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing avg85flx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/_usr_local_mydebs_._Packages, E:The package lists or status file could not be parsed or opened.'```
sudo apt-get update
``` returns the same error.

I tried to remove avg using sudo apt-get remove avg85flx, but that just returned the same error.

I'm unable to attach the contents of /var/lib/apt/lists/_usr_local_mydebs_._Packages.  because it's about 400k.  So here is the bit for avg, in case it's relevant.

> Package: avg85flx
Version: 8.5.287
Architecture: all
Essential: no
Maintainer: AVG
Installed-Size: 98990
Depends: 
Conflicts: avg71,avg75
Provides: avglinux
Filename: ./avg85flx-r287-a2632.i386.deb
Size: 70122576
MD5sum: e55d77b43aae7aaa43cfe0cc0dee89b9
Section: utils
Priority: optional
Description: AVG Anti-Virus for LinuxThanks for your help.

PS. I have no idea how those smilies got their way into this post.  I didn't put them there.

---

### Post by oldmankit on 2009-11-12
Fixed.

This line confused me: _usr_local_mydebs_._Packages
It should actually be /usr/local/mydebs/Packages.gz, or something like that.  The short solution is, I removed this 'offline repository' from sources.list, and the problem dissapeared.

The folder exists because I have created my own offline repository, which saves re-downloading files if I want to re-install them.  See this how-to:
[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

Something got corrupted in that personal repository, or the file Packages.gz.

To fix the error message, I simply removed that repository from sources.list, using system -> administration -> software sources -> 3rd party software -> uncheck:  file:/usr/local/mydebs ./

This fixed it.

I then deleted everything in this offline repository, removed the avg deb from /var/cache/apt/archives (in case that was part of the problem).  After re-copying all the packages in /var/cache/apt/archives to /usr/local/mydebs, re-scanning to create a new Packages.gz file (see howto), it is all working again.

---

