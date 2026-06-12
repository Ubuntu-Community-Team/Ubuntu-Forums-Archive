---
title: "Anonymous SMB share doesn't automount, authenticated does. Why?"
date: 2006-06-03
forum: General Help
---

### Post by pbb on 2006-06-03
I would like to auto-mount a Windows share, which is read/writeable by guest. I can't get this to work on bootup, but when manually entering "sudo mount -a" everything works great. My /etc/fstab contains the following line:

//p4-3000/D /media/fat smbfs guest,uid=peter,iocharset=utf8,codepage=unicode,unicode 0 0

While trying to find a solution, I discovered the following. The following line in /etc/fstab works great:

//p4-3000/c$ /media/test smbfs auto,username=administrator,password=xxx 0 0

With both lines in fstab, after bootup c$ is mounted and D is not. Manually entering "sudo mount -a" afterwards mounts D without any problems.

This seems to be related to the authentication. Does anybody have any suggestions?

For the technical details: I'm actually running Kubuntu 5.10 inside VMWare 5.5 running on top of Windows XP SP2, which is also the server I try to mount (p4-3000).

---

