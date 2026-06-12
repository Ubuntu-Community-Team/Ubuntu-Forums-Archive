---
title: "Having Apache access files from NTFS drive"
date: 2011-12-22
forum: General Help
---

### Post by play_ on 2011-12-22
Hello.

I set apache up, but my site's DocumentRoot points to files hosted in an NTFS drive, thus, i get permission denied when accessing [http://localhost](http://localhost)

How do i give apache access to my ntfs drive?
or how do i make my ntfs drive read/write for everyone? (i think this is the problem)

The drive is mounted under 'Shared'. ls gives:

> drwx------  1 lyrae lyrae 12288 2011-12-22 00:16 Shared

i tried chmod 0777 Shared. but it does not see to change the permission.

---

### Post by mcduck on 2011-12-22
Sure, it's a permission issue since the files and directories need to be readable by Apache. And no, chown/chmod won't work, NTFS isn't able to handle POSIX permissions, it simply has no way to store such information. Instead you'll have to define the owner and permissions for the whole drive in /etc/fstab.

(this should be OK for a testing/development server, but if it's an actual production server open to the outside network I would definitely recommend just keeping the files on a Linux filesystem instead so you can set them to more sane ownership & permissions. Actually I'd recommend that anyway if it's just possible, you'd save yourself from lots of troubles that way...)

---

### Post by play_ on 2011-12-22
> **mcduck said:**
> Sure, it's a permission issue since the files and directories need to be readable by Apache. And no, chown/chmod won't work, NTFS isn't able to handle POSIX permissions, it simply has no way to store such information. Instead you'll have to define the owner and permissions for the whole drive in /etc/fstab.

(this should be OK for a testing/development server, but if it's an actual production server open to the outside network I would definitely recommend just keeping the files on a Linux filesystem instead so you can set them to more sane ownership & permissions. Actually I'd recommend that anyway if it's just possible, you'd save yourself from lots of troubles that way...)

Thank you.
Solved it by mounting the ntfs drive with

sudo mount -t ntfs -o rw,auto,user,fmask=0022,dmast=0000 /dev/sdc1 /mnt/shared

and yes it's for internal testing only

---

