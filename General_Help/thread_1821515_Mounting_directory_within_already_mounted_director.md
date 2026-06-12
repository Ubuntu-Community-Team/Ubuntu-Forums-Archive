---
title: "Mounting directory within already mounted directory"
date: 2011-08-09
forum: General Help
---

### Post by Nattereri on 2011-08-09
I am curious if mounting a directory inside an already mounted directory is considered safe? I have done this on an Ubuntu server before but never thought to ask if it could cause problems.
 
An example:
 
/dev/mapper/Raid5-VMStorage on /var/lib/libvirt/images
/dev/mapper/Raid1-SpareStorage on /var/lib/libvirt/images/Workstations

---

### Post by Mark Phelps on 2011-08-09
Since you appear to be mounting separate volumes, this will be OK.

In fact, when you think about it, since everything ends up getting mounted somewhere under "/", you're basically doing this whenever you mount a volume.

---

### Post by AlphaLexman on 2011-08-09
Just note that if you un-mount the parent volume, you un-mount the child volume as well.

---

### Post by Nattereri on 2011-08-10
Thanks for the replies that is the information I was looking for. I shall have to make some changes to the directory scheme then.

---

