---
title: "Updating repositories..."
date: 2012-03-02
forum: General Help
---

### Post by nd456 on 2012-03-02
Can anyone help me to update Luminance (Qtpfsgui) from version 1.9? I can't find any repositories for the software center. Or is there a way to get it in a .deb?
Website for software: [http://qtpfsgui.sourceforge.net/](http://qtpfsgui.sourceforge.net/)
Thanks, Andy

---

### Post by imachavel on 2012-03-02
looking at that web site, I cannot seem to find a linux version to install that in besides fedora, maybe it just won't work. 

try this:

[http://www.jonespcrepair.com/site4/2011/11/04/install-luminance-hdr-on-ubuntu-11-10/](http://www.jonespcrepair.com/site4/2011/11/04/install-luminance-hdr-on-ubuntu-11-10/)

---

### Post by winh8r on 2012-03-02
Halfway down the page at [http://qtpfsgui.sourceforge.net/]("http://qtpfsgui.sourceforge.net/")

where it says:

> Users of Ubuntu 11.04 can find pre compiled binaries for i386.

[ luminance-hdr_2.1.0-2_i386.deb ]
[ libraw_0.13.8-2_i386.deb ]

They must also install the package libtiff_3.9.4-2_i386.deb provided.

hope this helps.

---

### Post by imachavel on 2012-03-02
ahhhh man... I was going to install it, then take a screen shot for you:


libraw-dev
libraw-dev: command not found
danel@danel-Dimension-4700:~$ sudo apt-get install libraw-dev
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libraw-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 352 kB of archives.
After this operation, 1,470 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libraw-dev i386 0.13.8-0ubuntu1 [352 kB]
Fetched 352 kB in 1s (177 kB/s)     
Selecting previously deselected package libraw-dev.
(Reading database ... 326130 files and directories currently installed.)
Unpacking libraw-dev (from .../libraw-dev_0.13.8-0ubuntu1_i386.deb) ...
Setting up libraw-dev (0.13.8-0ubuntu1) ...
danel@danel-Dimension-4700:~$ sudo apt-get install qt4-qmake libexiv2-dev libopenexr-dev fftw3-dev libtiff4-dev libqt4-dev g++ libgs10-dev libraw-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libfftw3-dev' instead of 'fftw3-dev'
E: Unable to locate package libgs10-dev
danel@danel-Dimension-4700:~$ sudo apt-get install qt4-qmake libexiv2-dev libopenexr-dev libfftw3-dev libtiff4-dev libqt4-dev g++ libgsl0-dev libraw-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
libraw-dev is already the newest version.
libtiff4-dev is already the newest version.
libtiff4-dev set to manually installed.
The following extra packages will be installed:
  libilmbase-dev libqt4-opengl-dev libqtwebkit-dev qt4-linguist-tools
Suggested packages:
  libexiv2-doc libmysqlclient-dev libpq-dev libsqlite3-dev qt4-dev-tools
  qt4-doc
The following NEW packages will be installed:
  libexiv2-dev libfftw3-dev libgsl0-dev libilmbase-dev libopenexr-dev
  libqt4-dev libqt4-opengl-dev libqtwebkit-dev qt4-linguist-tools qt4-qmake
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,457 kB of archives.
After this operation, 56.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libexiv2-dev i386 0.21.1-0ubuntu2 [1,225 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libfftw3-dev i386 3.2.2-1ubuntu2 [1,938 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libgsl0-dev i386 1.15+dfsg-1 [1,241 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libilmbase-dev i386 1.0.1-3build2 [195 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libopenexr-dev i386 1.6.1-4.1 [383 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main qt4-linguist-tools i386 4:4.7.4-0ubuntu8.1 [849 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main qt4-qmake i386 4:4.7.4-0ubuntu8.1 [1,225 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libqt4-dev i386 4:4.7.4-0ubuntu8.1 [2,361 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libqt4-opengl-dev i386 4:4.7.4-0ubuntu8.1 [17.7 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libqtwebkit-dev i386 2.2~2011week36-0ubuntu1 [23.0 kB]
Fetched 9,457 kB in 38s (249 kB/s)                                             
Selecting previously deselected package libexiv2-dev.
(Reading database ... 326148 files and directories currently installed.)
Unpacking libexiv2-dev (from .../libexiv2-dev_0.21.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package libfftw3-dev.
Unpacking libfftw3-dev (from .../libfftw3-dev_3.2.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgsl0-dev.
Unpacking libgsl0-dev (from .../libgsl0-dev_1.15+dfsg-1_i386.deb) ...
Selecting previously deselected package libilmbase-dev.
Unpacking libilmbase-dev (from .../libilmbase-dev_1.0.1-3build2_i386.deb) ...
Selecting previously deselected package libopenexr-dev.
Unpacking libopenexr-dev (from .../libopenexr-dev_1.6.1-4.1_i386.deb) ...
Selecting previously deselected package qt4-linguist-tools.
Unpacking qt4-linguist-tools (from .../qt4-linguist-tools_4%3a4.7.4-0ubuntu8.1_i386.deb) ...
Selecting previously deselected package qt4-qmake.
Unpacking qt4-qmake (from .../qt4-qmake_4%3a4.7.4-0ubuntu8.1_i386.deb) ...
Selecting previously deselected package libqt4-dev.
Unpacking libqt4-dev (from .../libqt4-dev_4%3a4.7.4-0ubuntu8.1_i386.deb) ...
Selecting previously deselected package libqt4-opengl-dev.
Unpacking libqt4-opengl-dev (from .../libqt4-opengl-dev_4%3a4.7.4-0ubuntu8.1_i386.deb) ...
Selecting previously deselected package libqtwebkit-dev.
Unpacking libqtwebkit-dev (from .../libqtwebkit-dev_2.2~2011week36-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libexiv2-dev (0.21.1-0ubuntu2) ...
Setting up libfftw3-dev (3.2.2-1ubuntu2) ...
Setting up libgsl0-dev (1.15+dfsg-1) ...
Setting up libilmbase-dev (1.0.1-3build2) ...
Setting up libopenexr-dev (1.6.1-4.1) ...
Setting up qt4-linguist-tools (4:4.7.4-0ubuntu8.1) ...
update-alternatives: using /usr/bin/lupdate-qt4 to provide /usr/bin/lupdate (lupdate) in auto mode.
update-alternatives: using /usr/bin/lrelease-qt4 to provide /usr/bin/lrelease (lrelease) in auto mode.
Setting up qt4-qmake (4:4.7.4-0ubuntu8.1) ...
update-alternatives: using /usr/bin/qmake-qt4 to provide /usr/bin/qmake (qmake) in auto mode.
Setting up libqt4-dev (4:4.7.4-0ubuntu8.1) ...
update-alternatives: using /usr/bin/moc-qt4 to provide /usr/bin/moc (moc) in auto mode.
update-alternatives: using /usr/bin/uic-qt4 to provide /usr/bin/uic (uic) in auto mode.
update-alternatives: warning: skip creation of /usr/share/man/man1/uic.1.gz because associated file /usr/share/man/man1/uic-qt4.1.gz (of link group uic) doesn't exist.
Setting up libqt4-opengl-dev (4:4.7.4-0ubuntu8.1) ...
Setting up libqtwebkit-dev (2.2~2011week36-0ubuntu1) ...
danel@danel-Dimension-4700:~$ cd qmake
bash: cd: qmake: No such file or directory
danel@danel-Dimension-4700:~$ cd downloads
bash: cd: downloads: No such file or directory
danel@danel-Dimension-4700:~$ cd home
bash: cd: home: No such file or directory
danel@danel-Dimension-4700:~$ cd Downloads
danel@danel-Dimension-4700:~/Downloads$ qmake
Usage: qmake [mode] [options] [files]

QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
  -project       Put qmake into project file generation mode
                 In this mode qmake interprets files as files to
                 be built,
                 defaults to *.c; *.ui; *.y; *.l; *.ts; *.xlf; *.qrc; *.h; *.hpp; *.hh; *.hxx; *.H; *.cpp; *.cc; *.cxx; *.C
                 Note: The created .pro file probably will 
                 need to be edited. For example add the QT variable to 
                 specify what modules are required.
  -makefile      Put qmake into makefile generation mode (default)
                 In this mode qmake interprets files as project files to
                 be processed, if skipped qmake will try to find a project
                 file in your current working directory

Warnings Options:
  -Wnone         Turn off all warnings; specific ones may be re-enabled by
                 later -W options
  -Wall          Turn on all warnings
  -Wparser       Turn on parser warnings
  -Wlogic        Turn on logic warnings (on by default)
  -Wdeprecated   Turn on deprecation warnings (on by default)

Options:
   * You can place any variable assignment in options and it will be     *
   * processed as if it was in [files]. These assignments will be parsed *
   * before [files].                                                     *
  -o file        Write output to file
  -d             Increase debug level
  -t templ       Overrides TEMPLATE as templ
  -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
  -help          This help
  -v             Version information
  -after         All variable assignments after this will be
                 parsed after [files]
  -norecursive   Don't do a recursive search
  -recursive     Do a recursive search
  -set <prop> <value> Set persistent property
  -query <prop>  Query persistent property. Show all if <prop> is empty.
  -cache file    Use file as cache           [makefile mode only]
  -spec spec     Use spec as QMAKESPEC       [makefile mode only]
  -nocache       Don't use a cache file      [makefile mode only]
  -nodepend      Don't generate dependencies [makefile mode only]
  -nomoc         Don't generate moc targets  [makefile mode only]
  -nopwd         Don't look for files in pwd [project mode only]
danel@danel-Dimension-4700:~/Downloads$ make
make: *** No targets specified and no makefile found.  Stop.
danel@danel-Dimension-4700:~/Downloads$ sudo make install
make: *** No rule to make target `install'.  Stop.
danel@danel-Dimension-4700:~/Downloads$ sudo apt-get install luminance-hdr-2.2.0.tar.bz2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package luminance-hdr-2.2.0.tar.bz2
E: Couldn't find any package by regex 'luminance-hdr-2.2.0.tar.bz2'
danel@danel-Dimension-4700:~/Downloads$ sudo apt-get install luminance-hdr-2.2.0Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package luminance-hdr-2.2.0
E: Couldn't find any package by regex 'luminance-hdr-2.2.0'


SOOOO close!

---

### Post by imachavel on 2012-03-02
sudo apt-get install libtiff_3.9.4-2_i386.deb
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libtiff_3.9.4-2_i386.deb
E: Couldn't find any package by regex 'libtiff_3.9.4-2_i386.deb'
danel@danel-Dimension-4700:~$ sudo apt-get install luminance-hdr-2.2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package luminance-hdr-2.2.0
E: Couldn't find any package by regex 'luminance-hdr-2.2.0'


Any idea what regex is?

---

### Post by imachavel on 2012-03-02
sorry to complicate that, THIS:

[http://sourceforge.net/projects/qtpfsgui/files/luminance/2.1.0/libraw_0.13.8-2_i386.deb/download](http://sourceforge.net/projects/qtpfsgui/files/luminance/2.1.0/libraw_0.13.8-2_i386.deb/download)

is much simpler, but when searching for it and finding it and opening it it doesn't give an error message but doesn't open. the

libraw_0.13.8-2_i386.deb

download install failed, saying it was of a bad quality. I'm not sure why exactly. Maybe other dependencies are required? This would be a very good reason though why luminescence won't open

oh it looks like libtiff needs to be installed before libraw can be installed, which are both needed to run luminance hdr

---

### Post by nd456 on 2012-03-03
First, thank you for all the responses.
Despite me trying I'm unable to install Luminance. I don't know how to compile from source, I think thats the most likely way of solving this... If someone could give me semi-detailed instructions it would be greatly appreciated.
Thanks, Andy
Edit: Just to clarify, I tried installing those 3 binaries and everything seems to be good right up until you click on the luminance icon... Then nothing happens...

---

### Post by nd456 on 2012-03-05
Bump.

---

