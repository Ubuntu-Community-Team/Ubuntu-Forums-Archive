---
title: "Cannot install Luminance"
date: 2012-06-08
forum: General Help
---

### Post by qwertyjjj on 2012-06-08
I am trying to install Luminance and downloaded the source code from their site, then exrcted it to the desktop.
However, it will not create the make file.
Ia m doing this:

sudo apt-get install qt4-qmake libexiv2-dev libopenexr-dev fftw3-dev libtiff4-dev libqt4-dev g++ libgsl0-dev
j-media-centre@jmediacentre-A880G:~$ cd Desktop
j-media-centre@jmediacentre-A880G:~/Desktop$ cd luminance-hdr-2.3.0.beta1
    qmake
    make
    sudo make install

At qmake, I just get a load of help files and make errors:

```

j-media-centre@jmediacentre-A880G:~/Desktop/luminance-hdr-2.3.0.beta1$ qmake
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
j-media-centre@jmediacentre-A880G:~/Desktop/luminance-hdr-2.3.0.beta1$ make
make: *** No targets specified and no makefile found. Stop.
j-media-centre@jmediacentre-A880G:~/Desktop/luminance-hdr-2.3.0.beta1$ 


```

---

### Post by 23dornot23d on 2012-06-08
Luminance is .... qtpfsgui

you can install it from the repos 

sudo apt-get install qtpfsgui

> 
root@keith-Aspire-7730ZG:/home/keith# aptitude install qtpfsgui
The following NEW packages will be installed:
  qtpfsgui 
0 packages upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
Need to get 1,442 kB of archives. After unpacking 3,117 kB will be used.
Get: 1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric/universe qtpfsgui amd64 1.9.3-1.1build2 [1,442 kB]
Fetched 1,442 kB in 2s (621 kB/s)    
Selecting previously deselected package qtpfsgui.
(Reading database ... 230171 files and directories currently installed.)
Unpacking qtpfsgui (from .../qtpfsgui_1.9.3-1.1build2_amd64.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up qtpfsgui (1.9.3-1.1build2) ...
Processing triggers for menu ...
                                         
root@keith-Aspire-7730ZG:/home/keith# 
unless its the Beta you are installing

[http://qtpfsgui.sourceforge.net/](http://qtpfsgui.sourceforge.net/)

**Linux**

 Linux users should ask their vendors for a pre-packaged binary.

I tried A alien conversion and although it appeared to work the program would not run 

```

root@keith-Aspire-7730ZG:/home/keith/Downloads# alien luminance-hdr-2.3.0.beta1-1.fc16.x86_64.rpm --scripts
luminance-hdr_2.3.0.beta1-2_amd64.deb generated
root@keith-Aspire-7730ZG:/home/keith/Downloads# gdebi luminance-hdr_2.3.0.beta1-2_amd64.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 


A graphical tool for creating and tone-mapping HDR images
 Luminance is a graphical program for assembling bracketed photos into High
 Dynamic Range (HDR) images.  It also provides a number of tone-mapping
 operators for creating low dynamic range versions of HDR images.
 .
 (Converted from a rpm package by alien version 8.85.)
Do you want to install the software package? [y/N]:y
(Reading database ... 230494 files and directories currently installed.)
Preparing to replace luminance-hdr 2.3.0.beta1-2 (using luminance-hdr_2.3.0.beta1-2_amd64.deb) ...
Unpacking replacement luminance-hdr ...
Setting up luminance-hdr (2.3.0.beta1-2) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'


```

---

### Post by mcduck on 2012-06-08
Instead of compiling from source yourself, I'd recommend using some PPA repository that includes up-to-date packages fro Luminance HDR. For example this one should work: [https://launchpad.net/~philip5/+ppa-packages]("https://launchpad.net/~philip5/+ppa-packages")

---

### Post by qwertyjjj on 2012-06-08
> **mcduck said:**
> Instead of compiling from source yourself, I'd recommend using some PPA repository that includes up-to-date packages fro Luminance HDR. For example this one should work: [https://launchpad.net/~philip5/+ppa-packages]("https://launchpad.net/~philip5/+ppa-packages")

How do I add the public key?

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EA8F35793D8809A

I did this but still get the error above on updating:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43C56F3F

---

