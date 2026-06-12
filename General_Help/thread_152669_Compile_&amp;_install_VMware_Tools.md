---
title: "Compile &amp; install VMware Tools"
date: 2006-03-30
forum: General Help
---

### Post by Jong on 2006-03-30
I'm running Ubuntu 5.10 as a guest OS on VMware, and want to install VMware Tools also. From other topics I see though it isn't exactly Plug&Play, especially not for a newbie :)

I have found these links, but I'm having a hard time figuring out what to do.

[http://www.ubuntuforums.org/archive/index.php/t-106722.html](http://www.ubuntuforums.org/archive/index.php/t-106722.html)
[http://www.vmware.com/community/thread.jspa?messageID=354101#354101](http://www.vmware.com/community/thread.jspa?messageID=354101#354101)
[http://www.ubuntux.org/installing-the-vmware-tools-into-ubuntu-5-04](http://www.ubuntux.org/installing-the-vmware-tools-into-ubuntu-5-04)
[http://www.ubuntuforums.org/showthread.php?t=128766&highlight=vmware+tools](http://www.ubuntuforums.org/showthread.php?t=128766&highlight=vmware+tools)

Apparently I need installing gcc first.
Done, I think so.

Next, compiling the VMware Tools distrib.
I'm stuck here...

Help much appreciated.

---

### Post by johnnymac on 2006-03-30
What kind of error are you getting when you attempt this?  Can you post the output?

---

### Post by Jong on 2006-03-30
Yes, of course, should have included that in the first place, stupid.

I'd find another [guide]("https://lists.ubuntu.com/archives/ubuntu-users/2004-October/007022.html") which I followed.

However at #11, where it says to "Build and install the vmware tools", I'm stucked.

I'm pretty sure I'm doing something wrong, but what I cannot tell.

./vmware-install.pl returns the following error:

bash: ./vmware-install.pl: /usr/src/linux-headers-2.6.12 9 386/include/perl: bad interpreter: no such file or directory exists.

I have checked twice, and I'm in the right directory, and the file does exist.

As mentioned before, I'm new to Ubuntu, but if I'm not mistaken, shouldn't I in some way build up a kernel or compile the libs before I can install?

---

### Post by Jong on 2006-04-20
Problem solved, the solution turned out to be pretty simple :)

The error message from #3 says it all. The install file, vmware-install.pl, cannot find the perl directory, because it points to a wrong location.

All I did was to open vmware-install.pl and correct the very first line.

---

