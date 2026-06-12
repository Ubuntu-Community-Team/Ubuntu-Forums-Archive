---
title: "Blender and network share mountpoint-permissions"
date: 2009-12-10
forum: General Help
---

### Post by Dieter_C on 2009-12-10
Hallo,

I'm using blender 2.43 for quite a while now on Ubuntu 8.10
Now, i'm doing some tests with blender 2.49 on Ubuntu 9.10. Blender works fine but i can acces my files on my fileserver.

The shared directory from the server (win2003) is mounted on a directory in my home directory (~/mountpoint) All mount options are defined in fstab. Access to de directory works fine r+w

But in blender i see the mountpoint as an empty file. While in ubuntu 8.10 this worked fine.

The first difference i've seen are the permissions on the mountpoint.

on ubuntu 8.10 drwxrwxwx 
on ubuntu 9.10 drwxr-xr-x 

I'm the owner so there should be no problem.

Is this a problem with blender or do i need 777 on the mountpoint to have this working.


Thanks in advance,


Regards Dieter

---

