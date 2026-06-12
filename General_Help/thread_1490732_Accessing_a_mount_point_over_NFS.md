---
title: "Accessing a mount point over NFS"
date: 2010-05-22
forum: General Help
---

### Post by Listerofsmeg01 on 2010-05-22
I have a folder shared over NFS that contains three sub folders:
 
(Machine A)
[FONT=Courier New]**/usr/nfsshare/a**[/FONT]
[FONT=Courier New]**/usr/nfsshare/b**[/FONT]
[FONT=Courier New]**/usr/nfsshare/c**[/FONT]
 
I can see these three folders just fine on machine B via nfs.
[FONT=Courier New]**sudo mount machineA:/usr/nfsshare /mnt/ShareMountOnB**[/FONT]
 
Now I want to mount a second drive in machine A, and mount it as a fourth shared folder:
**[FONT=Courier New]mkdir /usr/nfsshare/d[/FONT]**
**[FONT=Courier New]sudo mount /dev/sdb1 /usr/nfsshare/d[/FONT]**
 
I can see and access all four folders on machine A just fine.
 
I can SEE all four folders on machine B in /mnt/ShareMountOnB, but when I descend into folder d, it is empty!
 
Bizarrely I can create files in this empty folder d on machine B, but I have no idea where they are being held. They are certainly not in machine A.
 
Can anyone explain what is going on, and what I have to do to access the real contents of folder d. I have already changed all permissions and owners to be identical to the other folders.
 
(ps. Sharing it over samba to a Windows PC works fine)
 
Many thanks,
Lister

---

### Post by Listerofsmeg01 on 2010-05-22
OK nevermind, I've sorted it.
 
Looks like NFS deliberately doesn't export the contents of any mounted subfolders. There appears to be a "nohide" option to turn this behaviour off, but it didn't work for me.
 
I got around it by just exporting and mounting each of the four folders explicitly.

---

