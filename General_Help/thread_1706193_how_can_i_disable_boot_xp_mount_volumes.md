---
title: "how can i disable boot xp mount volumes"
date: 2011-03-13
forum: General Help
---

### Post by Gianmaria on 2011-03-13
Hi

i'm new
today i discovered ubuntu and i love it!!!

i have some problems

ubuntu on boot mount all my NTFS volume , and i'm a bit worried about this , outside my floppy :(

by the way **this is no**t the point

i would love to know if there is a **gui **that help me to edit the startup/boot actions

i mean what should perform ubuntu in the boot startup

i'm looking for a gui (i prefer a gui then the console because i don't know how use it :( ) that help me to  manage it


1) i would like to disable -> mount my ntfs volumes


2) in the future i would like  to enable it again , i mean mount my ntfs volumes


now i would like to disable

is there a gui (program) that let me to edit the startup?

i'm really a novice

thanks
cheers

---

### Post by wilee-nilee on 2011-03-13
Are you sure the XP is mounted, it should show but the stock install of Ubuntu does not include a auto mount you have to set that up.

Look in home in the side bar and look if the XP is actually mounted does a little line with a triangle appear next to the XP in the side panel when you click it sf so that is when it is mounted.

---

### Post by YesWeCan on 2011-03-13
Would you post the output of
**cat /etc/fstab**

This file lists all the partitions that are automatically mounted at boot time.

There is a GUI for selecting applications that are run at start-up: look in the System/Preferences menu.

---

### Post by Gianmaria on 2011-03-13
> **wilee-nilee said:**
> Are you sure the XP is mounted, it should show but the stock install of Ubuntu does not include a auto mount you have to set that up.

Look in home in the side bar and look if the XP is actually mounted does a little line with a triangle appear next to the XP in the side panel when you click it sf so that is when it is mounted.
i have under the menu bar place a list of my volumes , fa32 included 
if i click on them i can see inside
only the floppy is gray

---

### Post by wilee-nilee on 2011-03-13
> **Gianmaria said:**
> i have under the menu bar place a list of my volumes , fa32 included 
if i click on them i can see inside
only the floppy is gray

Post the fstab as YesWeCan suggests that will tell us what's up.

They mount when you click on them; if you right click the XP and unmount it will unmount.

If you give a more specifics on what you want done at boot it would be helpful. The startup applications in preference as suggested is a auto start and a way to turn off things you don't want to run then.

---

### Post by Gianmaria on 2011-03-13
> **wilee-nilee said:**
> Post the fstab as YesWeCan suggests that will tell us what's up.

They mount when you click on them; if you right click the XP and unmount it will unmount.

If you give a more specifics on what you want done at boot it would be helpful. The startup applications in preference as suggested is a auto start and a way to turn off things you don't want to run then.
terminal->**cat /etc/fstab**

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=7abf60ab-44f4-4642-9949-61e63dc98965 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
is this?

---

