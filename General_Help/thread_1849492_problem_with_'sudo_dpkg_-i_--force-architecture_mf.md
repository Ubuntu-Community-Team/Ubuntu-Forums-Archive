---
title: "problem with 'sudo dpkg -i --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb'"
date: 2011-09-24
forum: General Help
---

### Post by Deguerrilla on 2011-09-24
I am running a 64bit  Dell studio

I have been attempting to get my Brother MFC6490CW to work with my Ubuntu OS. I have been stumped for months now and would like some help.

The following is the msg that i received when i tried to
 "sudo dpkg -i --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb"

start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb
myserver@mycomputer-numer:~$ sudo dpkg -i --force-architecture mfc6490cwcupswrapper-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 210778 files and directories currently installed.)
Preparing to replace mfc6490cwcupswrapper 1.1.2-2 (using mfc6490cwcupswrapper-1.1.2-2.i386.deb) ...
cups start/running, process 20781
Unpacking replacement mfc6490cwcupswrapper ...
dpkg: dependency problems prevent configuration of mfc6490cwcupswrapper:
 mfc6490cwcupswrapper depends on mfc6490cwlpr; however:
  Package mfc6490cwlpr is not installed.
dpkg: error processing mfc6490cwcupswrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mfc6490cwcupswrapper


How do i get around this error

---

### Post by sumski on 2011-09-24
mfc6490cwcupswrapper depends on mfc6490cwlpr; however:
  **Package mfc6490cwlpr is not installed**.

---

### Post by garvinrick4 on 2011-09-24
> [COLOR=Black]dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
[/COLOR] [COLOR=Red][COLOR=Black]Why --force[/COLOR]

[/COLOR]

---

### Post by Deguerrilla on 2011-09-24
I have attempted to install mfc6490cwlpr... 
the following is the error i get continuously

'sudo dpkg -i --force-architecture  mfc6490cwlpr-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 210778 files and directories currently installed.)
Preparing to replace mfc6490cwlpr 1.1.2-2 (using mfc6490cwlpr-1.1.2-2.i386.deb) ...
Unpacking replacement mfc6490cwlpr ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb
Myserver@mycomputer-Studio-1737:~$ sudo dpkg -i --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 210778 files and directories currently installed.)
Preparing to replace mfc6490cwlpr 1.1.2-2 (using mfc6490cwlpr-1.1.2-2.i386.deb) ...
Unpacking replacement mfc6490cwlpr ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb'

---

### Post by garvinrick4 on 2011-09-24
You are trying to install a 32 bit .deb when you have a 64 bit system.
Get the 64 bit .deb build and install it.

---

### Post by Deguerrilla on 2011-09-24
Correct but i cant seem to find the 64bit packages.
I have read that Force architecture is the way to get around this.
of course that hasn't proven to be true.

any more suggestions?

Also i have installed ia32-libs

---

