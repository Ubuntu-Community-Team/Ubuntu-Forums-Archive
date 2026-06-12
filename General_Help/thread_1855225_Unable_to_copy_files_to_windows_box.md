---
title: "Unable to copy files to windows box"
date: 2011-10-05
forum: General Help
---

### Post by zer0net on 2011-10-05
Hello,
I'm trying to copy some files from ubuntu to windows file server (NTFS), I get error "file cannot be handled because you do not have permission to read it". 
is it even possible to do what i'm trying to do?

Thank you

---

### Post by t4thfavor on 2011-10-05
It sounds related to permissions, other than that, yes you can move files between linux and windows in many ways including over the network,

what type of transfer are you attempting, does your user have permission to read the files, and does the server have apropriate permissions to allow you to write to the target directory?

---

### Post by collisionystm on 2011-10-05
Where are you trying to copy the files from?

---

### Post by zer0net on 2011-10-05
hi thank you for reply,
i'm trying to copy some from home folder and some from root folder over the network to a shared folder on a windows box.

EDIT: I am using 
```
gksudo nautilus
```
but still unable to copy files.

---

### Post by t4thfavor on 2011-10-05
Check that you have the proper access to the local files to read them. Also check remote folder for proper permissions.

---

### Post by zer0net on 2011-10-05
> **t4thfavor said:**
> Check that you have the proper access to the local files to read them. Also check remote folder for proper permissions.

I did right click the folder and change the owner to my name, but still I am unable to do so.

---

### Post by t4thfavor on 2011-10-05
You are probably going to need to open the share with gksudo as well. I seem to remember issues when dragging files between root instances of nautilus, and non-root ones.

---

### Post by zer0net on 2011-10-08
> **t4thfavor said:**
> You are probably going to need to open the share with gksudo as well. I seem to remember issues when dragging files between root instances of nautilus, and non-root ones.

how do i do that?

---

### Post by t4thfavor on 2011-10-08
Look up how to mount the smb share using fstab, or with alt-F2 gksu nautilus and navigate to the share using that.

---

