---
title: "Access Fedora partition from Ubuntu"
date: 2010-12-24
forum: General Help
---

### Post by satish_j on 2010-12-24
I can mount the windows partition within ubuntu from Nautilus with Read/Write access,but not able to do so for Fedora partition.
Fedora partition is getting mounted from Nautilus,but when i try to access the home folder of any Fedora user,it gives the permission denied error.
Any ideas how to get around this?

---

### Post by Verbeck on 2010-12-24
you'll have to chmod it to 774 or 776 so that others can access it

edit: or run nautilus as root

---

### Post by satish_j on 2010-12-24
> **Verbeck said:**
> you'll have to chmod it to 774 or 776 so that others can access it

edit: or run nautilus as root

you mean:
Login to fedora,change the chmod rights of the fedora directory,then login to Ubuntu and access it
OR
Login to Ubuntu,mount the Fedora partition, and change the chmod rights of directory required
??

---

### Post by Verbeck on 2010-12-24
should work either way

---

### Post by Morbius1 on 2010-12-24
The only problem I can see with that ( chmod 77x ) is that if you write something to the partition from Ubuntu you will likely not be able to write to it from Fedora even if your login name is the same. Morbius on Ubuntu will have a uid=1000 while Morbius on Fedora will be uid=500 ( I think ). Morbius ( Ubuntu ) does not equal Morbius ( Fedora ).

---

### Post by jroa on 2010-12-24
> **Morbius1 said:**
> The only problem I can see with that ( chmod 77x ) is that if you write something to the partition from Ubuntu you will likely not be able to write to it from Fedora even if your login name is the same. Morbius on Ubuntu will have a uid=1000 while Morbius on Fedora will be uid=500 ( I think ). Morbius ( Ubuntu ) does not equal Morbius ( Fedora ).

You can fix this with the permissions, right?

---

### Post by satish_j on 2010-12-24
> **Morbius1 said:**
> The only problem I can see with that ( chmod 77x ) is that if you write something to the partition from Ubuntu you will likely not be able to write to it from Fedora even if your login name is the same. Morbius on Ubuntu will have a uid=1000 while Morbius on Fedora will be uid=500 ( I think ). Morbius ( Ubuntu ) does not equal Morbius ( Fedora ).

I did not get it..
If i write something to an windows folder,i can also access/edit it in windows,then why not for Fedora partition?
Do you mean mounting of NTFS and ext4 partitions are handled differently??

---

### Post by Morbius1 on 2010-12-24
> You can fix this with the permissions, right?After the fact and only as root. And that could get tedious after a while depending on how the Fedora partition is being used from Ubuntu.
> If i write something to an windows folder,i can also access/edit it in windows,then why not for Fedora partition?
Do you mean mounting of NTFS and ext4 partitions are handled differently??           4 Minutes Ago 08:14 AMYes they are. NTFS and FAT32 are mounted in such a way that they inherit the ownership and permissions of the mount point itself. Linux doesn't do that. You can approximate that using sticky bits and setting up a new  group on both Fedora and Ubuntu but then you're doing some major tinkering with both systems here.

---

### Post by Verbeck on 2010-12-24
> **Morbius1 said:**
> You can approximate that using sticky bits and setting up a new  group on both Fedora and Ubuntu but then you're doing some major tinkering with both systems here.
why not just change the user id to the same thing?

---

### Post by Morbius1 on 2010-12-24
> **Verbeck said:**
> why not just change the user id to the same thing?
Agreed, that's another option.

---

