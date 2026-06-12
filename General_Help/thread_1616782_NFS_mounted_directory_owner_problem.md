---
title: "NFS mounted directory owner problem"
date: 2010-11-08
forum: General Help
---

### Post by emreakbas on 2010-11-08
I am able to mount an NFS directory as a regular user (which doesn't have sudo rights) because a suitable entry (i.e. with the user option) is defined in /etc/fstab file.

But, when I mount it, I am not the owner of it! The owner is the default superuser of the system. So I don't have write permissions in the mounted directory.

How can I make the directory mine?

---

### Post by Hippytaff on 2010-11-08
Look into chown :-)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by emreakbas on 2010-11-08
nope. Neither  "chown" nor "sudo chown" works. I get permission denied.

---

### Post by SeijiSensei on 2010-11-08
What are the ownership and permissions on the exported directory on the NFS server itself?  Do you have the identical user and group IDs on both machines?

Try "ls -ln" on the mounted directory.  Do you see the same numerical user and group IDs as you do if you run the same command on the server?

---

### Post by emreakbas on 2010-11-08
The user-ids on the server and the client are different.

---

