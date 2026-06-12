---
title: "/host permissions are 777"
date: 2009-07-21
forum: General Help
---

### Post by orsenthil on 2009-07-21
I have ubuntu installed through wubi. The windows files are accessible at /host partition. 
But I find the permissions of /host, the sub-directories within /host and all the files therein to be too permissive.

Every directory is drwxrwxrwx
Every file is rwxrwxrwx

With the user:group as root:root

Why is this so?   I doubt, if this normally acceptable by unix users. 

What would be good permissions to setup for windows partition under Wubi?

---

### Post by The Cog on 2009-07-21
NTFS cannot store unix permissions, so they have to be emulated. You can specify the user, group and umask (inverse of permissions) in the /etc/fstab file that controls filesystem mounting. For example, options umask=222 will make all the files and directories look like permissons 555, r-xr-xr-x.

---

### Post by tomatosquid on 2009-08-01
I don't think /host is listed in fstab after wubi install. How can you change permissions? I can envisage my kids accidentally deleting the contents of the windows partition...

---

### Post by orsenthil on 2009-08-24
Yes, /host is not listed under /etc/fstab, I am reluctant to manually add /host and set the options to umask=222.
Did you have any luck?

---

### Post by kunev on 2010-11-26
So this is just a hanging issue for now?
I'm using Ubuntu 10.10 and there seems to be no way to chmod on /host. It doesn't seem very Linux like to have this problem...

Has anyone tried adding to  the fstab file, or is it very recomendable not to play around with it?

---

