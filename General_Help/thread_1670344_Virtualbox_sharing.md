---
title: "Virtualbox sharing"
date: 2011-01-18
forum: General Help
---

### Post by MikeBeveridge on 2011-01-18
G'day, I have done searching on "the google", however I have a specific issue that I hope someone can help with.
 
Host machine is Win7 64bit, Guest is ubuntu. We have a folder on the host (C:/Shared) and are able to mount the folder using sudo mount -t vboxsf etc etc and this folder mounts fine in ubuntu. However the permissions on the shared folder in ubuntu has changed. The owner is now root and access is read only. I have tried to Chmod and even chown but it never does anything.
 
We want to transfer files from ubuntu(guest) to the win7 (host).
 
Any ideas would be greatly appreciated!!.
 
cheers
 
 
Mike

---

### Post by MikeBeveridge on 2011-01-27
Found the issue,  As usual it is simple.  The permissions on the folder in Win7 were screwy.  Deleted the folder and started again.  All good.

---

