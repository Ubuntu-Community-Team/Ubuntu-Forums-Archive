---
title: "How do I mount an NTFS drive with full permissions"
date: 2010-07-22
forum: General Help
---

### Post by nmyrick on 2010-07-22
The issue I am having is that Virtual Box does not recognize my USB drives.  I understand that it is related to the fact that Ubuntu cannot recognize the permissions on the USB NTFS drive.  So how do I mount the ntfs drive and gain full permissions?

One post suggested that I have to join my user to the 'vbuser' group in users and groups to fix this in 9.04, but I do not have a "vbuser" group in my list of groups.  I am running 10.04.

---

### Post by todak on 2010-07-22
If you installed Virtualbox from the repositories, it will not have USB support. To get that, you must download the non-free version from vitrualbox.org. The differences between the free and non-free (non-free having nothing to do with cost) can be discerned here: [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by techunit on 2010-07-22
> **todak said:**
> If you installed Virtualbox from the repositories, it will not have USB support. To get that, you must download the non-free version from vitrualbox.org. The differences between the free and non-free (non-free having nothing to do with cost) can be discerned here: [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)
This is correct you need the so called non-free version of Virtualbox to get the USB support. I didn't realize this at first either.

---

