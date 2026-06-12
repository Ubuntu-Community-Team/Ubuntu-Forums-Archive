---
title: "Installing git using checkinstall"
date: 2010-11-30
forum: General Help
---

### Post by victor.zamanian on 2010-11-30
Hello!

I'm trying to install git (git-scm.com) from source. I need apt to recognize that it's installed, so I figured I would install it using the checkinstall program.

I followed the steps listed in the following thread: 
[http://ubuntuforums.org/showthread.php?t=1554991](http://ubuntuforums.org/showthread.php?t=1554991)

Unfortunately, I'm getting some errors. I wondering if anyone could tell me what I'm doing wrong. Full log:


```

$ wget http://kernel.org/pub/software/scm/git/git-1.7.3.2.tar.bz2
$ tar xf git-1.7.3.2.tar.bz2
$ cd git-1.7.3.2
$ make prefix=/usr/local
$ sudo checkinstall -D --install=no --maintainer=victor.zamanian@gmail.com --pkgname=git-core --pkgversion=1:1.7.3.2 --provides=git --requires=libc6,libcurl3-gnutls,libdigest-sha1-perl,liberror-perl,libexpat1,perl-modules,zlib1g make prefix=/usr/local install install-man

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>>     

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ victor.zamanian@gmail.com ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ git-core ]
3 -  Version: [ 1:1.7.3.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ git-1.7.3.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [ libc6,libcurl3-gnutls,libdigest-sha1-perl,liberror-perl,libexpat1,perl-modules,zlib1g ]
11 - Provides: [ git ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make prefix=/usr/local install install-man...

========================= Installation results ===========================
    SUBDIR git-gui
    SUBDIR gitk-git
make[1]: Nothing to be done for `all'.
    SUBDIR perl
    SUBDIR git_remote_helpers
    SUBDIR templates
install -d -m 755 '/usr/local/bin'
install -d -m 755 '/usr/local/libexec/git-core'
install   git-fast-import git-imap-send git-shell git-show-index git-upload-pack git-http-backend git-http-fetch git-http-push git-daemon git-remote-http git-remote-https git-remote-ftp git-remote-ftps git-am git-bisect git-difftool--helper git-filter-branch git-lost-found git-merge-octopus git-merge-one-file git-merge-resolve git-mergetool git-pull git-quiltimport git-rebase--interactive git-rebase git-repack git-request-pull git-stash git-submodule git-web--browse git-add--interactive git-difftool git-archimport git-cvsexportcommit git-cvsimport git-cvsserver git-relink git-send-email git-svn git-remote-testgit git-instaweb '/usr/local/libexec/git-core'
install -m 644  git-mergetool--lib git-parse-remote git-sh-setup '/usr/local/libexec/git-core'
install git git-upload-pack git-receive-pack git-upload-archive git-shell git-cvsserver '/usr/local/bin'
make -C templates DESTDIR='' install
make[1]: Entering directory `/home/victor/git-1.7.3.2/templates'
install -d -m 755 '/usr/local/share/git-core/templates'
(cd blt && tar cf - .) | \
	(cd '/usr/local/share/git-core/templates' && umask 022 && tar xof -)
tar: ./info/exclude: Cannot utime: No such file or directory
tar: ./info: Cannot utime: No such file or directory
tar: ./description: Cannot utime: No such file or directory
tar: ./hooks/applypatch-msg.sample: Cannot utime: No such file or directory
tar: ./hooks/post-update.sample: Cannot utime: No such file or directory
tar: ./hooks/pre-commit.sample: Cannot utime: No such file or directory
tar: ./hooks/prepare-commit-msg.sample: Cannot utime: No such file or directory
tar: ./hooks/post-commit.sample: Cannot utime: No such file or directory
tar: ./hooks/commit-msg.sample: Cannot utime: No such file or directory
tar: ./hooks/post-receive.sample: Cannot utime: No such file or directory
tar: ./hooks/pre-rebase.sample: Cannot utime: No such file or directory
tar: ./hooks/pre-applypatch.sample: Cannot utime: No such file or directory
tar: ./hooks/update.sample: Cannot utime: No such file or directory
tar: ./hooks: Cannot utime: No such file or directory
tar: Exiting with failure status due to previous errors
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/victor/git-1.7.3.2/templates'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

---

### Post by andrewthomas on 2010-11-30
you seemed to have skipped ```
./configure
```

---

### Post by victor.zamanian on 2010-11-30
According to the INSTALL file with the git distribution, I shouldn't need to ./configure. Please see that file for more information. Also note the "$ make prefix=/usr/local" command.

This is neither here nor there since I get the same errors when trying to run checkinstall whether I use ./configure first or just make first.

---

### Post by mc4man on 2010-11-30
You should try adding this to your checkinstall command
```
--fstrans=no
```
If that works, (or for general use of checkinstall), go to /etc/checkinstallrc
and edit this line, change blue to 0
> # Are we going to use filesystem translation?
TRANSLATE=[COLOR="Blue"]1[/COLOR]

I change a few other like 'accept defaults', ect.

If you package is successful run this afterwards, may not be needed, never hurts
sudo ldconfig

Edit
with the source you have and using checkinstall I think you can just use 1 command - ( it will re-build from checkinstall so no need to do twice
from a cleaned or fresh source

```
sudo checkinstall -D --install=no --maintainer=victor.zamanian@gmail.com --pkgname=git-core \
--pkgversion=1:1.7.3.2 --provides=git --default --backup=no --deldoc=yes --deldesc=yes \
--requires=libc6,libcurl3-gnutls,libdigest-sha1-perl,liberror-perl,libexpat1,perl-modules,zlib1g \
--fstrans=no --delspec=yes make prefix=/usr/local install all
```

---

### Post by victor.zamanian on 2010-12-01
> **mc4man said:**
> You should try adding this to your checkinstall command
```
--fstrans=no
```
If that works, (or for general use of checkinstall), go to /etc/checkinstallrc
and edit this line, change blue to 0

Thanks! It worked by adding that flag. I checked the man page and it says:

```
       --fstrans Enable/disable filesystem translation. Filesystem translation
                 enabled causes the install to proceed in a  temporary  direc&#8208;
                 tory, thus not actually touching your system.
```

I'm a little confused. Why did it fail when I had this enabled before, but it worked with this disabled?


> **mc4man said:**
> I change a few other like 'accept defaults', ect.

Ah. Would you mind posting your settings file here for me?

> **mc4man said:**
> with the source you have and using checkinstall I think you can just use 1 command - ( it will re-build from checkinstall so no need to do twice
from a cleaned or fresh source

```
sudo checkinstall -D --install=no --maintainer=victor.zamanian@gmail.com --pkgname=git-core \
--pkgversion=1:1.7.3.2 --provides=git --default --backup=no --deldoc=yes --deldesc=yes \
--requires=libc6,libcurl3-gnutls,libdigest-sha1-perl,liberror-perl,libexpat1,perl-modules,zlib1g \
--fstrans=no --delspec=yes make prefix=/usr/local install all
```

Yes, it did re-build all the sources again even though I had already built the sources. Why is this?

Thanks for your help!

---

