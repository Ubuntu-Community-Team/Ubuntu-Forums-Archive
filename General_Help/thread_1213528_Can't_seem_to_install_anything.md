---
title: "Can't seem to install anything"
date: 2009-07-14
forum: General Help
---

### Post by mavis311 on 2009-07-14
I'm new to ubuntu, not _as_ new to linux, and have tons of winblows experience.  I just installed ubuntu 9.04 today.  Admittedly I know almost nothing about linux at this stage, but I think I should know enough to get some things to work.  I know how to use the terminal, and I know how to extract archives and stuff, so I won't list most of that stuff.

I love the terminal, so I read about tilda.  My problem starts where I try to install tilda.  Let me know if I'm going about this all wrong!  I read the INSTALL.  I already had a terminal window open and I issued the command "./configure".  Lots and lots of "checking..." messages until I get this error: "configure: error: No lex program found".  

Quick search on the web doesn't really turn up too much, but I find I should install libConfuse and vte.  I download libConfuse, and "./configure".  Even more "checking..."s, and it ./configures just fine.  Now I "make".  Here are the last few lines of the output:
lexer.c:1585: error: 'input' defined but not used
make[2]: *** [lexer.lo] Error 1
make[2]: Leaving directory `/home/mavis/Downloads/confuse-2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mavis/Downloads/confuse-2.6'
make: *** [all] Error 2

Getting frustrated.  Thought the buzz on the street was how great and easy this was supposed to be...  Don't mind having to do some work, computers don't run themselves, but it seems it is all for naught.

Download latest vte I can find.  "./configure" until errors: 
checking for intltool >= 0.35.0... ./configure: line 13050: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

"found found"?? whatever.  that's exactly how it is on my terminal.  I'll try something I've used on my windows machines for a couple of years now, the last.fm "scrobbler."  (it's sort of like pandora I'm told, but I don't really know if it's better or not, I've never used pandora.)  Download, extract, ./configure: 
==> Last.fm Configure 
==> Checking for qmake... 
==> Checking the installed version of Qt is correct... 
./configure: line 40: -v: command not found
Your version of Qt seems to be too old, we require Qt 4.3 or above.

It is possible you have Qt3 and Qt4 both installed. Locate your qt4 installation
and ensure it is placed first in the path, eg:

    PATH=/opt/qt4/bin:$PATH ./configure

However this configure script is very basic, perhaps we got it wrong..
Try typing the following, perhaps it will build for you :)

    qmake -config release && make

Don't know how to check current version...  I'll just download the newest one.  Download, extract, ./configure:
Creating qmake. Please wait...
g++ -c -o project.o -pipe -DQMAKE_OPENSOURCE_EDITION -I. -Igenerators -Igenerators/unix -Igenerators/win32 -Igenerators/mac -I/home/mavis/Downloads/qt-4.5.2/include -I/home/mavis/Downloads/qt-4.5.2/include/QtCore -I/home/mavis/Downloads/qt-4.5.2/src/corelib/global -I/home/mavis/Downloads/qt-4.5.2/src/script -DQT_NO_PCRE -DQT_BUILD_QMAKE -DQT_BOOTSTRAPPED -DQT_NO_TEXTCODEC -DQT_NO_UNICODETABLES -DQT_NO_COMPONENT -DQT_NO_STL -DQT_NO_COMPRESS -I/home/mavis/Downloads/qt-4.5.2/mkspecs/linux-g++ -DHAVE_QCONFIG_CPP -DQT_NO_THREAD -DQT_NO_QOBJECT -DQT_NO_GEOM_VARIANT  project.cpp
make: g++: Command not found
make: *** [project.o] Error 127

I do know how to check the version of gcc I have.  It is version 4.3.3.  Not too old. 

Also, when firefox tries to install adobe flash or one of the other two .swf players listed, I get error "Could not find package 'whatever-package'".

So, that was too long, sorry.  I hope I'm just doing something stupid and easy to fix.  Any suggestions?

---

### Post by aysiu on 2009-07-14
Is there something wrong with pasting in this command? ```
sudo apt-get update && sudo apt-get install tilda flashplugin-nonfree
``` This may help you, too:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by alphacrucis2 on 2009-07-14
> **mavis311 said:**
> I'm new to ubuntu, not _as_ new to linux, and have tons of winblows experience.  I just installed ubuntu 9.04 today.  Admittedly I know almost nothing about linux at this stage, but I think I should know enough to get some things to work.  I know how to use the terminal, and I know how to extract archives and stuff, so I won't list most of that stuff.

I love the terminal, so I read about tilda.  My problem starts where I try to install tilda.  Let me know if I'm going about this all wrong!  I read the INSTALL.  I already had a terminal window open and I issued the command "./configure".  Lots and lots of "checking..." messages until I get this error: "configure: error: No lex program found".  

Quick search on the web doesn't really turn up too much, but I find I should install libConfuse and vte.  I download libConfuse, and "./configure".  Even more "checking..."s, and it ./configures just fine.  Now I "make".  Here are the last few lines of the output:
lexer.c:1585: error: 'input' defined but not used
make[2]: *** [lexer.lo] Error 1
make[2]: Leaving directory `/home/mavis/Downloads/confuse-2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mavis/Downloads/confuse-2.6'
make: *** [all] Error 2

Getting frustrated.  Thought the buzz on the street was how great and easy this was supposed to be...  Don't mind having to do some work, computers don't run themselves, but it seems it is all for naught.

Download latest vte I can find.  "./configure" until errors: 
checking for intltool >= 0.35.0... ./configure: line 13050: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

"found found"?? whatever.  that's exactly how it is on my terminal.  I'll try something I've used on my windows machines for a couple of years now, the last.fm "scrobbler."  (it's sort of like pandora I'm told, but I don't really know if it's better or not, I've never used pandora.)  Download, extract, ./configure: 
==> Last.fm Configure 
==> Checking for qmake... 
==> Checking the installed version of Qt is correct... 
./configure: line 40: -v: command not found
Your version of Qt seems to be too old, we require Qt 4.3 or above.

It is possible you have Qt3 and Qt4 both installed. Locate your qt4 installation
and ensure it is placed first in the path, eg:

    PATH=/opt/qt4/bin:$PATH ./configure

However this configure script is very basic, perhaps we got it wrong..
Try typing the following, perhaps it will build for you :)

    qmake -config release && make

Don't know how to check current version...  I'll just download the newest one.  Download, extract, ./configure:
Creating qmake. Please wait...
g++ -c -o project.o -pipe -DQMAKE_OPENSOURCE_EDITION -I. -Igenerators -Igenerators/unix -Igenerators/win32 -Igenerators/mac -I/home/mavis/Downloads/qt-4.5.2/include -I/home/mavis/Downloads/qt-4.5.2/include/QtCore -I/home/mavis/Downloads/qt-4.5.2/src/corelib/global -I/home/mavis/Downloads/qt-4.5.2/src/script -DQT_NO_PCRE -DQT_BUILD_QMAKE -DQT_BOOTSTRAPPED -DQT_NO_TEXTCODEC -DQT_NO_UNICODETABLES -DQT_NO_COMPONENT -DQT_NO_STL -DQT_NO_COMPRESS -I/home/mavis/Downloads/qt-4.5.2/mkspecs/linux-g++ -DHAVE_QCONFIG_CPP -DQT_NO_THREAD -DQT_NO_QOBJECT -DQT_NO_GEOM_VARIANT  project.cpp
make: g++: Command not found
make: *** [project.o] Error 127

I do know how to check the version of gcc I have.  It is version 4.3.3.  Not too old. 

Also, when firefox tries to install adobe flash or one of the other two .swf players listed, I get error "Could not find package 'whatever-package'".

So, that was too long, sorry.  I hope I'm just doing something stupid and easy to fix.  Any suggestions?

There is probably no need to compile anything. Just install tilda from the repos. Applications - Add/Remove programs or use synaptic package manager under System - Administration. If you really do need to compile something that hasn't already been packaged then first you need to install the build-essential package from the terminal:

```
sudo apt-get install build-essential
```

To get flash, see here:

[URL="http://www.psychocats.net/ubuntu/flash"]
http://www.psychocats.net/ubuntu/flash[/URL]

---

### Post by mavis311 on 2009-07-14
No, there appears to be nothing wrong with that command....  It installed flash ok and deferred to update manager afterward...  I just checked for updates a little while ago inside X and the um said there were none available.  Every other "sudo..." I've tried hasn't worked.  I can't duplicate the error right now... Perhaps because system is updating?

Is there info at psychocats that will explain what I'm doing with that sudo command?  I'd really like to understand linux instead of just regurgitating commands like that.

---

### Post by mavis311 on 2009-07-14
> **alphacrucis2 said:**
> There is probably no need to compile anything. Just install tilda from the repos.

Ok, then...  That brings to mind two questions:
a.) why is everything I download via web only in source format?
b.) what are "repos"?

---

### Post by aysiu on 2009-07-14
**sudo**
with root (or administrative) privileges

**apt-get**
using the software package manager

**update**
get the latest list of available software repository packages

**&&**
if the last command completes successfully, run the next command

**sudo**
with root privileges

**apt-get**
use the package manager

**install**
to install the following packages

**tilda flashplugin**
tilda and the Adobe Flash player plugin

The link I posted above explains what repos are.

---

### Post by Vaphell on 2009-07-14
sudo gives superuser priviledges to modify system files/directories. You work as an ordinary user and are free to do anything in your home dir, but accessing system stuff requires root rights - sudo in front of a command lets you execute it with them.

repositories are libraries of software packages tuned for a given distro. You don't have to compile anything manually, just mark checkbox next to the package name in synaptic (UI for installing stuff from repos) and apply. Sources are for die-hards, not recommended for novice users

---

### Post by drs305 on 2009-07-14
And if psychocat's site isn't enough, here is the Ubuntu wiki explaining the repositories:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by jerome1232 on 2009-07-14
Canonical maintains some online repositories of software pre-packaged for Ubuntu, The Ubuntu community also maintains some online repositories, all together there are thousands of programs pre-packaged in these repositories.

The Synaptic Package Manager(System-Administration-Synaptic Package Manager) is a gui tool used to browse the software available to you, this is the by far vastly prefered method of installing.

Apt-get is the cli method of accessing these repositories, you can see how much easier these methods are to use.

The few programs which may not be in the repositories maintianed by Ubuntu usually maintain their own repositories which you can add and synaptic will be able to manage those as well.

Compiling from source is a last ditch effort usually only used to get the bleeding edge latest version of software, no pre-packaged form is available, or if you need to make customizations to the program itself.

You should check out psychocats guide linked earlier I believe it explains most of this.

---

### Post by alphacrucis2 on 2009-07-14
> **mavis311 said:**
> Ok, then...  That brings to mind two questions:
a.) why is everything I download via web only in source format?
b.) what are "repos"?

Ubuntu is based on Debian which uses a package system. Ubuntu provides software repositories which have gazillions of pre-packaged programs for you to download. To see what repositories you are accessing see System - Administration - Software sources. If you haven't changed anything it will have the defaults. As well as the Ubuntu ones you can set up third party ones. A Debian package is in the form of a .deb file which you can also install just by double clicking on the file. The simplest way to install one of the pre set up packages is as I said. From the menu - Applications Add/Remove. The apps are categorised but you can also enter an app name in the search field if you know what it is. You can also run the synaptic package manager from system - administration which gives you more control over what is going on with package installation. Finally you can do it from the command line using 

sudo apt-get install <package name>

If you really must then you can compile from source as explained here:
[URL="https://help.ubuntu.com/community/CompilingSoftware"]
https://help.ubuntu.com/community/CompilingSoftware[/URL]

---

### Post by mavis311 on 2009-07-14
repos = repositories.  thanks.

I still have a bit of lingo to learn, eh?

Thanks a lot, all of you, for your assistance.  I imagine I'll need some more in the days and weeks to come.  I'm so excited to get back into linux!!!  The last time I used linux it was some RedHat distribution, not sure what version, it was about 10 years ago, though.  Xwindow never would run on my machine then...

So, why is it that when I go to the software originator's website I can only download a tarball of source?  

I'm used to writing and compiling code on a dos or windows platform, just not so much on linux, yet.  I'm all but fed up with MS's BS, so I'm hoping to make a permanent switch to linux.  Or at least to use it 85% of the time or more and try to put windows behind me.

---

### Post by alphacrucis2 on 2009-07-15
> **mavis311 said:**
> repos = repositories.  thanks.


So, why is it that when I go to the software originator's website I can only download a tarball of source?  



Possibly because the author doesn't bother to provide a package. The common package formats are Debian and variants - .deb files. Redhat and variants use .rpm files. You will find that some sites do offer their software pre-packaged for various distro's but even for the ones that don't, you often find that the Ubuntu community has done the packaging job for most popular programs, even if they are not officially supported by Ubuntu.

---

### Post by mavis311 on 2009-07-15
I see.  Wow, if the response I've gotten from this forum is any indication of what using ubuntu linux will be like, I think I'm going to enjoy it!  Thanks again, y'all!

If anyone can answer this last bit, I think this thread could be put to rest.

Why I couldn't seem to install anything via "sudo apt-get install whatever-package" prior to using the sudo command string that aysiu gave me?

---

### Post by aysiu on 2009-07-15
> **mavis311 said:**
> I see.  Wow, if the response I've gotten from this forum is any indication of what using ubuntu linux will be like, I think I'm going to enjoy it!  Thanks again, y'all!

If anyone can answer this last bit, I think this thread could be put to rest.

Why I couldn't seem to install anything via "sudo apt-get install whatever-package" prior to using the sudo command string that aysiu gave me?
Because ```
sudo apt-get update
``` checks to see what packages are available to install off the online software repositories (or "repos").

---

### Post by mavis311 on 2009-07-15
> **aysiu said:**
> Because ```
sudo apt-get update
``` checks to see what packages are available to install off the online software repositories (or "repos").


Ok... So, i couldn't install anything via sudo b/c there was no information on my machine regarding repos available online until I issued the command "sudo apt-get update"??

---

### Post by aysiu on 2009-07-15
> **mavis311 said:**
> Ok... So, i couldn't install anything via sudo b/c there was no information on my machine regarding repos available online until I issued the command "sudo apt-get update"??
Yes.

Basically, in Ubuntu (and most Linux distributions), software is managed by the package manager. The package manager keeps track of what you have installed and also checks with some online servers to see what they have available for you to install.

*apt-get* is the main command to access the package manager (graphical versions are Synaptic, Add/Remove, Update Manager, and GDebi).

With *apt-get update*, you tell the package manager to look for what's available on the servers to install.

With *apt-get install*, you then specify what you would to install from the servers.

---

### Post by mavis311 on 2009-07-15
Wonderful!  I love this forum.

Thanks again all!  And a special thanks to you, aysiu!

---

