---
title: "I get errors every time I try to install a package"
date: 2010-07-29
forum: General Help
---

### Post by paulwis on 2010-07-29
I've recently noticed that whenever I try to install a package via the package manager in ubuntu 10.04, the installation fails. This is really annoying and I don't know how to fix it =\ I've looked at other forum posts but none really quite answer the issue. I get the following error from synaptic:

"E: global: subprocess installed post-installation script returned error exit status 1"

Then in the terminal (i tried to install 3dchess as a test):

Selecting previously deselected package xaw3dg.
(Reading database ... 171991 files and directories currently installed.)
Unpacking xaw3dg (from .../xaw3dg_1.5+E-17build1_i386.deb) ...
Selecting previously deselected package 3dchess.
Unpacking 3dchess (from .../3dchess_0.8.1-16_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up global (5.7.1-1) ...
hostname: Name or service not known
dpkg: error processing global (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up xaw3dg (1.5+E-17build1) ...

Setting up 3dchess (0.8.1-16) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 global
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up global (5.7.1-1) ...
hostname: Name or service not known
dpkg: error processing global (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 global



Browsing the forums, it seemed that maybe I was having hostname issues. Here is the output of the following:
paul@paul-laptop:~$ hostname
paul-laptop
paul@paul-laptop:~$ hostname --fqdn
hostname: Name or service not known

Maybe something to take into consideration is that I'm using the mvps.org hosts file as my hosts file (a very nice way to block ads and viruses). Would this be causing problems? I don't have a server and all issues with hostname --fqdn are from people trying to host things and have static dns names. I don't want that, I just want to be able to install things again!! :(

---

### Post by philinux on 2010-07-29
What you got in /etc/hosts.

---

### Post by paulwis on 2010-07-29
What I have in my hosts file is the one from this site:
[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

You can check it out there. It's quite large so I'd rather not paste it. The important thing though is the first line is still "127.0.0.1 localhost"

---

### Post by philinux on 2010-07-29
> **paulwis said:**
> What I have in my hosts file is the one from this site:
[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

You can check it out there. It's quite large so I'd rather not paste it. The important thing though is the first line is still "127.0.0.1 localhost"

But you need the second line too.
127.0.1.1    paul-laptop

---

### Post by paulwis on 2010-07-29
YES! You are the MAN! Adding the 127.0.1.1 line did the trick, I never knew you had to do that. Thank you so much!

---

