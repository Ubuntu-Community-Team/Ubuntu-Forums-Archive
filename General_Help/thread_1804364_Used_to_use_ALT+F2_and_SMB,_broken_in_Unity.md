---
title: "Used to use ALT+F2 and SMB://, broken in Unity?"
date: 2011-07-14
forum: General Help
---

### Post by pctx on 2011-07-14
So--- I about ripped my hair as I've moved up from 10.10 to 11.04 today and I found that Unity cannot pass a simple SMB:// command to get to my windows servers.

I finally read a thread on here stating to run natalius and magically it prompted me for password and I connected.

Is this a feature of 11.04 or am I going insane?

---

### Post by bryanl on 2011-07-14
smbfs isn't usually installed by default so if you want to mount cifs or use smbmount or whatever, make sure it is installed. I use autofs to mount the Windows shares and always have to remember to install smbfs as well.

Nautilus uses gvfs to mount the file shares and has been doing so for quite a while. You'll find the mount point at ~/.gvfs after you access it in Nautilus.

---

