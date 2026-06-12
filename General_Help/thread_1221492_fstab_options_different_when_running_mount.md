---
title: "fstab options different when running mount"
date: 2009-07-23
forum: General Help
---

### Post by Q345 on 2009-07-23
Hi all,

I have a second SATA drive connected to my box.  It worked fine by automounting (? it was listed in the Places menu and appeared on the desktop when selected) but I wanted it to mount on boot.  I added the following to /etc/fstab:

/dev/sdb1    /media/DISK2    auto    rw,suid,exec,auto,user,async 0    2

but when I run the "mount" command the options are different:

/dev/sdb1 on /media/DISK2 type ext3 (rw,noexec,nosuid,nodev)

What's causing that?

---

### Post by plucky on 2009-07-24
> **Q345 said:**
> Hi all,

I have a second SATA drive connected to my box.  It worked fine by automounting (? it was listed in the Places menu and appeared on the desktop when selected) but I wanted it to mount on boot.  I added the following to /etc/fstab:

/dev/sdb1    /media/DISK2    auto    rw,suid,exec,auto,user,async 0    2

but when I run the "mount" command the options are different:

/dev/sdb1 on /media/DISK2 type ext3 (rw,noexec,nosuid,nodev)

What's causing that?


I think it is because the **user** option in the list means it defaults to noexec,nosuid and nodev.You need to move the user option further up the list and then put suid,exec after to override i.e
```
/dev/sdb1    /media/DISK2    auto    rw,user,suid,exec,auto,async 0    2
``` well that is my interpretation.

Good Luck

---

### Post by dcstar on 2009-07-24
> **Q345 said:**
> Hi all,

I have a second SATA drive connected to my box.  It worked fine by automounting (? it was listed in the Places menu and appeared on the desktop when selected) but I wanted it to mount on boot.  I added the following to /etc/fstab:

/dev/sdb1    /media/DISK2    **auto**    rw,suid,exec,auto,user,async 0    2

but when I run the "mount" command the options are different:

/dev/sdb1 on /media/DISK2 type ext3 (rw,noexec,nosuid,nodev)

What's causing that?

Auto mean auto - if you want specific options mount it as a particular type with the options that can apply to that type.

---

### Post by Q345 on 2009-07-24
Thanks Plucky!

That fixed it!  :)

---

