---
title: "FAT Partitions under Removable Media not mounted on boot"
date: 2009-08-11
forum: General Help
---

### Post by popcorn09 on 2009-08-11
I installed Ubuntu 9.04. The FAT32 and NTFS partitions of my dual boot laptop are listed under removable media but they are not mounted at boot time. If I click on any of these partitions, then it is mounted and the drive opens.

I tried editing /etc/fstab with the following line for a partition:
```
/dev/sda8	  /media/E  vfat user,umask=0222,rw,auto,exec,utf8 0 2 
```

The partition now gets mounted on boot but is read-only for the user logged in. The directory /media/E is owned by user, not root. :confused:

How do I configure partitions to mount at boot without being read-only for users?
The automatic list that is populated under Places->Removable Media, how can I edit that?

Please help.
Thanks.

---

### Post by dcstar on 2009-08-12
> **popcorn09 said:**
> I installed Ubuntu 9.04. The FAT32 and NTFS partitions of my dual boot laptop are listed under removable media but they are not mounted at boot time. If I click on any of these partitions, then it is mounted and the drive opens.

I tried editing /etc/fstab with the following line for a partition:
```
/dev/sda8	  /media/E  vfat user,umask=0222,rw,auto,exec,utf8 0 2 
```

The partition now gets mounted on boot but is read-only for the user logged in. The directory /media/E is owned by user, not root. :confused:

How do I configure partitions to mount at boot without being read-only for users?
The automatic list that is populated under Places->Removable Media, how can I edit that?

Please help.
Thanks.

Install the **pysdm **package and use that to configure things.

---

### Post by popcorn09 on 2009-08-14
Pysdm doesn't work properly. It shows only 2 out of 4 partitions. Only the two are edited, the rest two just do not work. I had to uninstall it and remove its pref changes. 

Is there any other way to make this work?

---

### Post by P4man on 2009-08-14
try editing fstab using this:
> 
/dev/sda8 /media/E vfat defaults 1 0


---

### Post by popcorn09 on 2009-08-15
> **P4man said:**
> try editing fstab using this:

It does not work. Still mounts as read only for the user. 

I can't believe there is no solution for this in Ubuntu, it used to be so user-friendly, what happened?!

---

### Post by popcorn09 on 2009-08-15
Found the solution here
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Would have been good if someone had just pointed me to it. 
Thanks anyway!

---

