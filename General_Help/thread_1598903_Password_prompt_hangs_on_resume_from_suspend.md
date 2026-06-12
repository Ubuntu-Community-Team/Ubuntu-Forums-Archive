---
title: "Password prompt hangs on resume from suspend"
date: 2010-10-17
forum: General Help
---

### Post by alohiageek on 2010-10-17
(I already posted this as a bug on launchpad using ubuntu-bug 5 days ago, but I've had no reply so far)

Binary package hint: gdm

Version of Ubuntu: 10.10 (Upgraded from 10.04, which was upgraded from 9.10).
Version of Package: gdm 2.30.5-0ubuntu4

Information: When the system resumes from Suspend or Hibernate, a box appears, requesting my password. When I type this, it says "Checking...", and hangs. In order to get to the desktop, I have to get to a terminal from CTRL+ALT+F1, and type 'sudo service gdm stop && sudo service gdm start'. This gets me to a desktop, but this starts a new session, and all windows and documents open before the system suspended or hibernated are gone.

What I expected to happen: I type my password, it takes a moment to check it, and then I reach the desktop, with all windows still open.

Thank you

ProblemType: Bug
DistroRelease: Ubuntu 10.10
Package: gdm 2.30.5-0ubuntu4
ProcVersionSignature: Ubuntu 2.6.32-24.43-generic 2.6.32.15+drm33.5
Uname: Linux 2.6.32-24-generic i686
NonfreeKernelModules: prl_vtdhook nvidia
Architecture: i386
Date: Tue Oct 12 22:12:19 2010
InstallationMedia: Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
ProcEnviron:
 LC_TIME=en_GB.UTF-8
 PATH=(custom, user)
 LANG=en_GB.utf8
 SHELL=/bin/bash
SourcePackage: gdm

---

