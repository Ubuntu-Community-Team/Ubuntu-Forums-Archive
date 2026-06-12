---
title: "Disallow access to Windows 7 partition"
date: 2011-05-14
forum: General Help
---

### Post by brwiese on 2011-05-14
I have Windows 7 and Ubuntu 10.04 installed on the same harddrive. I'm using grub to boot both. I would like to deny access to the windows partitions, but allow access to removable drives and shared drives.

Thanks,

---

### Post by dcstar on 2011-05-14
> **brwiese said:**
> I have Windows 7 and Ubuntu 10.04 installed on the same harddrive. I'm using grub to boot both. I would like to deny access to the windows partitions, but allow access to removable drives and shared drives.


You will probably have to mount the Windows partition in /etc/fstab (or use the **pysdm** package) and then use the **noauto** option in the fstab line.

---

### Post by llamabr on 2011-05-14
> **brwiese said:**
> I have Windows 7 and Ubuntu 10.04 installed on the same harddrive. I'm using grub to boot both. I would like to deny access to the windows partitions, but allow access to removable drives and shared drives.

Thanks,

Deny access to whom?  To someone logged in remotely?  There is nothing you can do to completely lock down a machine, if you let someone else sit in front of it.

The above advice will direct grub not to mount it automatically.

---

