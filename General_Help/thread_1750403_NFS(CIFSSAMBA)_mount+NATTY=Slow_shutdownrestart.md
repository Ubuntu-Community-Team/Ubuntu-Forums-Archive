---
title: "NFS(CIFS|SAMBA) mount+NATTY=Slow shutdown|restart?"
date: 2011-05-05
forum: General Help
---

### Post by deckoff on 2011-05-05
I had this problem - slow shutdown with Ubuntu when NAF mounted in /etc/fstab. Not big news, It is well known problem, I managed to fix it somehow, adding a simple script to umount the drive while restarting/ shutting down. K02 links in rc0.d rc1.d and rc6.d.
Somehow this is now broken in Natty - the system will shutdown forever. It seems the problem is either new version of upstart ( less probable) or bug in libc6 which stops the umount script, cause libc6 upgrade causes umount to fail on shutdown because init cannot be restarted ([http://osdir.com/ml/ubuntu-bugs/2011-04/msg37484.html)]("http://osdir.com/ml/ubuntu-bugs/2011-04/msg37484.html")
Does anyone know a fix for it. It seem to me, a downgrade of libc6 is possible, but I dont know how to do it....
Please, share knowledge and opinion...

---

### Post by stefan.hattrell on 2011-09-20
Bump.

---

### Post by Stonedancer on 2011-10-06
I have the same problem but I don't use scripts I just have to wait 2 minutes for the laptop to complete it's shut down where it would take 5 seconds without the fstab cifs entry. 

A long term solution for this is needed. Can't Ubuntu sort their distro so that it unmounts network mounts BEFORE it tries to terminate the OS? :(

---

