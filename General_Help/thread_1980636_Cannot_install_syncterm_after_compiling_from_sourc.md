---
title: "Cannot install syncterm after compiling from source"
date: 2012-05-15
forum: General Help
---

### Post by Corey Goettsch on 2012-05-15
Hello,

I was trying to install the BBS program syncterm from source, and it would not finish.  I had successfully compiled the program, but when I ran sudo checkinstall, I got the following output from the terminal:

nicholas@nicholas-Inspiron-1545:/usr/local/src/syncterm-20120515/src/syncterm$ sudo checkinstall
[sudo] password for nicholas: 

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> Syncterm 
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "SyncTERM" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ root@nicholas-Inspiron-1545 ]
1 -  Summary: [ An ANSI-BBS terminal which supports telnet, rlogin, and SSH ]
2 -  Name:    [ syncterm ]
3 -  Version: [ 0.9.4 ]
4 -  Release: [ 20071001 ]
5 -  License: [ GPL ]
6 -  Group:   [ Applications/Communications ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ syncterm ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ syncterm ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make -C ../../3rdp/build cryptlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/3rdp/build'
make[1]: Nothing to be done for `cryptlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/3rdp/build'
make -C ../xpdev mtlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/src/xpdev'
make[1]: Nothing to be done for `mtlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/src/xpdev'
make -C ../conio mtlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/src/conio'
make[1]: Nothing to be done for `mtlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/src/conio'
make -C ../uifc mtlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/src/uifc'
make[1]: Nothing to be done for `mtlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/src/uifc'
Linking gcc.linux.x64.exe.debug/syncterm
gzip < syncterm.man > syncterm.1.gz
mkdir -p /usr/local/bin
mkdir -p /usr/local/share/applications
mkdir -p /usr/local/man/man1
mkdir: cannot create directory `/usr/local/man': File exists
make: [installdirs] Error 1 (ignored)
mkdir -p /usr/local/share/icons/hicolor/64x64/apps
Installing...
install gcc.linux.x64.exe.debug/syncterm /usr/local/bin
install -m 0444 syncterm.png /usr/local/share/icons/hicolor/64x64/apps
install -m 0444 syncterm.desktop /usr/local/share/applications
install -m 0444 syncterm.1.gz /usr/local/man/man1
install: cannot create regular file `/usr/local/man/man1': No such file or directory
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

nicholas@nicholas-Inspiron-1545:/usr/local/src/syncterm-20120515/src/syncterm$ sudo checkinstall --fstrans=0

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "SyncTERM" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ root@nicholas-Inspiron-1545 ]
1 -  Summary: [ An ANSI-BBS terminal which supports telnet, rlogin, and SSH ]
2 -  Name:    [ syncterm ]
3 -  Version: [ 0.9.4 ]
4 -  Release: [ 20071001 ]
5 -  License: [ GPL ]
6 -  Group:   [ Applications/Communications ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ syncterm ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ syncterm ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make -C ../../3rdp/build cryptlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/3rdp/build'
make[1]: Nothing to be done for `cryptlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/3rdp/build'
make -C ../xpdev mtlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/src/xpdev'
make[1]: Nothing to be done for `mtlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/src/xpdev'
make -C ../conio mtlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/src/conio'
make[1]: Nothing to be done for `mtlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/src/conio'
make -C ../uifc mtlib
make[1]: Entering directory `/usr/local/src/syncterm-20120515/src/uifc'
make[1]: Nothing to be done for `mtlib'.
make[1]: Leaving directory `/usr/local/src/syncterm-20120515/src/uifc'
Linking gcc.linux.x64.exe.debug/syncterm
mkdir -p /usr/local/bin
mkdir -p /usr/local/share/applications
mkdir -p /usr/local/man/man1
mkdir: cannot create directory `/usr/local/man': File exists
make: [installdirs] Error 1 (ignored)
mkdir -p /usr/local/share/icons/hicolor/64x64/apps
Installing...
install gcc.linux.x64.exe.debug/syncterm /usr/local/bin
install -m 0444 syncterm.png /usr/local/share/icons/hicolor/64x64/apps
install -m 0444 syncterm.desktop /usr/local/share/applications
install -m 0444 syncterm.1.gz /usr/local/man/man1
install: cannot create regular file `/usr/local/man/man1': No such file or directory
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

Can anyone please tell me what this error means?  I'm quite new to compiling software--I've actually never successfully done it.  This is the closest I've gotten: there are usually dependency problems, and I give up.  I would really appreciate your help.  

Sincerely,

Corey Goettsch

---

