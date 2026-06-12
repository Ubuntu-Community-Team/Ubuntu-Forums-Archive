---
title: "Mount drive that is mounted on another Ubuntu system"
date: 2010-06-19
forum: General Help
---

### Post by fontzter on 2010-06-19
Hi, I have been having the hardest time with this.  I am trying to mount a share on a Ubuntu 10.04 system from another Ubuntu 10.04 system.

The system with the share has the OS on one drive and then data on a second internal sata drive that is mounted.  The share is on this second drive.

I can see it when I browse networking from the other system but it won't mount.  I get a message saying that the folder contents can't be displayed.  I do not have permissions necessary to view the contents...

I have tried setting the share folder permissions as permissive as possible but can't get passed it.

Any help would be appreciated.

Thanks,

Dave

---

### Post by louieb on 2010-06-19
I use NFS heres how - [HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

For Linux to Linux it pretty easy to setup and works a lot smoother that samba.

---

