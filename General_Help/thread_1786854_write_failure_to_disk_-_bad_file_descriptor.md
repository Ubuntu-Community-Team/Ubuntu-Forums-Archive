---
title: "write failure to disk - bad file descriptor"
date: 2011-06-20
forum: General Help
---

### Post by i2dave on 2011-06-20
Hi

I'm running a backup routine from a Solaris 10 box, using ufsdump, to an ubuntu 10.04 server.  This was working fine up until a few days ago, when the ubuntu server was upgraded, and reinstalled, and I'm now getting the following error when the ufsdump process is trying to write to the server:

DUMP: write: Bad File Descriptor
DUMP: Write error 0 blocks into volume 1

The ufsdump process is initiated from the backup server (ubuntu) via an rsh command, which then runs the ufsdump process to remotely write back to the server.  This should present no problems, and has been fine until the rebuild!

Any thoughts?

I'd really like to know why the dump process thinks the file descriptor is bad and refuses to write to the disk!  Is there something I can do with the mounted disk?

The disk is mounted rw on an ext3 filesystem, and there are no issues with using rcp or tar to write to it (but I want to persevere with dump if poss.)

Thanks

---

### Post by gmargo on 2011-06-20
> **i2dave said:**
> This was working fine up until a few days ago, when the ubuntu server was upgraded, and reinstalled

...

via an rsh command

Probably the **rsh-server** package was not reinstalled.

---

### Post by i2dave on 2011-06-21
I installed rsh-redone-server, which includes rsh-server et al, bug-fixed.

There's no issue with rsh'ing back to the ubuntu system, because (as mentioned) rcp, tar and rsh are working fine.

It's just the ufsdump on the Solaris side that seems to have developed the issue.

It's unfortunate, because the Solaris servers are working OK, and there are no plans to retire them yet, so I have to be able to use them for backups :(

---

### Post by dFlyer on 2011-06-21
Have you tried testing the disk with disk utilities?

---

### Post by i2dave on 2011-06-21
Yep - all checks out OK

It's frustrating, because the previous incarnation of the ubuntu server (running 9.04 upgraded to 10.04 via system upgrades) was working OK, so there was obviously something within the system that didn't flag this as a problem!

Whether it was incumbant with 9.04 and simply inherited, or something else I don't know.

The problem is I can't get at the old server's disk to analyse its settings.....

Is there a way to configure / check / analyse the file descriptors on a disk / server ?

It seems any attempts to write to the server using Solaris' ufsdump are rejected - perhaps Solaris is now seen as defunct, so is rejected by ubuntu? ](*,)

---

