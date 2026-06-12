---
title: "Changing file access"
date: 2011-04-03
forum: General Help
---

### Post by nkae100 on 2011-04-03
I have a file owned by root, but other people are able to view it. How can I stop this?

---

### Post by dcstar on 2011-04-03
> **nkae100 said:**
> I have a file owned by root, but other people are able to view it. How can I stop this?

Change the "Others" permission to "None".

---

### Post by nkae100 on 2011-04-03
I do this as root, but the setting reverts back automatically.

---

### Post by dcstar on 2011-04-03
> **nkae100 said:**
> I do this as root, but the setting reverts back automatically.

If the file is in a System folder, then the underlying security system may not allow changes to it.

---

### Post by nkae100 on 2011-04-03
The file is located in /mnt/... - my Windows partition.

---

### Post by dhyonz on 2011-04-03
use terminal
then type this command

sudo chmod -rwx (your file name)

that means, no one can read that file except super user (root)

---

### Post by nkae100 on 2011-04-03
I tried that command as root, but other users other than root can still access the file.

---

### Post by matt_symes on 2011-04-03
Hi

> **nkae100 said:**
> The file is located in /mnt/... - my Windows partition.

This is an NTFS or FAT32 file system ? 

You will not be able to use chmod et al if it is. They are Linux permissions. Do you mount it in fstab ?

Kind regards

---

### Post by Rebelli0us on 2011-04-03
I've had that too. Linux has no security on NTFS partitions. But there is a solution, see this thread here:

[http://ubuntuforums.org/showthread.php?t=1587386]("http://ubuntuforums.org/showthread.php?t=1587386")
See post with "umask=077", kind of geeky but it works.

---

### Post by matt_symes on 2011-04-03
Hi

> **Rebelli0us said:**
> I've had that too. Linux has no security on NTFS partitions. But there is a solution, see this thread here:

[http://ubuntuforums.org/showthread.php?t=1587386]("http://ubuntuforums.org/showthread.php?t=1587386")
See post with "umask=077", kind of geeky but it works.

Yes. That is the solution if it's a windows file system. He will need to edit his /etc/fstab file.

He can also look at ACL's if he needs more fine grained control.

Kind regards

---

