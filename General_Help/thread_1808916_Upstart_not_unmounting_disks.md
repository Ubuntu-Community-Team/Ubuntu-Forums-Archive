---
title: "Upstart not unmounting disks"
date: 2011-07-20
forum: General Help
---

### Post by wd5gnr on 2011-07-20
Very frustrated. I have used Unix for ages so I understood the SysV startup stuff. But I have not had a lot of luck with Upstart. 

The other day I noticed that on every reboot my disks are getting fsck'd. I just recently put an ext2 on /tmp so this takes a while (the ext4 drives just rip through their journals).

The problem is no one is unmounting them on a KDE restart (4.X). I started out looking at /etc/init.d/umountfs and putting some logging in there. It never runs. This is despite that /etc/init has an upstart job that is supposed to run all the runlevel stuff.

I also tried to log some info in /etc/init/mountall-shell.conf which looks like it tries to do a umount -a on shutdown (which is probably not a good idea;  you need to unmount in a particular order). That doesn't seem to happen either.

I am not even sure how to troubleshoot this further. I suppose I need to see if the reboot(8) command has the same problem. Or if I shut down kdm first if it goes away.

Any ideas at all?

---

### Post by wd5gnr on 2011-07-25
Hmm... no traction on this and I can't help but wonder if I'm the only one seeing this problem.

There was talk on launchpad about a similar problem but it was supposedly fixed. 

Does anyone know if sysv is supposed to unmount the disks or upstart? Neither seems to be doing it.

---

