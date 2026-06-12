---
title: "How is it possible to mount without root priveleges?"
date: 2011-07-01
forum: General Help
---

### Post by adit on 2011-07-01
> If a device/partition is not listed in fstab ONLY ROOT may mount the device/partition.
Some of my partitions are not listed in /etc/fstab.  But I can mount them by clicking in nautilus "Places" menu.  How is it possible I can mount *without root privileges*.

---

### Post by Dangertux on 2011-07-01
By default mount/umount run with SUID , and can be used by users that are "sudoers"

That is how. This of course can be changed if you'd like

---

### Post by ahears on 2011-07-01
> **adit said:**
> Some of my partitions are not listed in /etc/fstab.  But I can mount them by clicking in nautilus "Places" menu.  How is it possible I can mount *without root privileges*.
  
Try adding yourself the privilege in **System >> Administration >> Users and Groups >> Advanced Settings >> User Privileges >> Mount User Space File Systems (FUSE).**

---

### Post by Morbius1 on 2011-07-01
>                               If a device/partition is not listed in fstab ONLY ROOT may mount the device/partition.                      Prior to 10.04 that statement is correct. After 10.04 it is not because Ubuntu made it so by it's configuration of policykit. It you would like to return to being prompted for credentials then you can change policykit yourself: [http://ubuntuforums.org/showpost.php?p=9445234&postcount=7](http://ubuntuforums.org/showpost.php?p=9445234&postcount=7)

---

### Post by AlexandreMBM on 2013-02-21
**PolicyKit**. Control at */usr/share/polkit-1/actions/org.freedesktop.udisks.policy* file. See how [here]("http://ubuntu.paslah.com/policykit/").

---

### Post by wildmanne39 on 2013-02-21
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

