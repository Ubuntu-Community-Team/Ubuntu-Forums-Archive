---
title: "Opening certain software apps causing Ubuntu to shutdown"
date: 2010-12-27
forum: General Help
---

### Post by DavidG24 on 2010-12-27
Hi guys,

I just installed Ubuntu 10.10 64bit. I installed VirtualBox ( AMD64 bit version) from here ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)) however whenever I went to run it, it would cause the system to log out (not shut down, just drop out) and return to the login screen.

I thought this could be an issue with that version of VirtualBox so I uninstalled and and then installed the version through the Software Centre, however unfortunately it was causing the same problem. I thought this may be a VirtualBox specific issue, however the same thing is now happening since I installed skype (again only when I run Skype).

I understand the description I am giving is very vague, and as such my first question would be : how am I able to produce an error report (of such) that would better suffice in describing the problem?
second question : Obviously, if anyone has come across this problem, do they know how to fix it?

Sorry, one last thing, and I'm not sure if this matters at all, but I'm running three monitors over two video cards using the Nvidia driver with Xinerema. I only bring this up, because a while back I was running 10.04 with two monitors in Twinview and had no problems..

Any help would be greatly appreciated,

David

---

### Post by jason102 on 2011-01-11
Hey David,

I'm having the same problem too, but it appears to be an issue with X and the Nvidia drivers conflicting. Unless we switch back to twinview (meaning no rotated monitor for me), we can't run those programs until the X/Nvidia problem is sorted out. Read the following thread...
[http://forums.virtualbox.org/viewtopic.php?f=7&t=35298](http://forums.virtualbox.org/viewtopic.php?f=7&t=35298)

---

