---
title: "Where are my partitions and data stored on them"
date: 2009-08-15
forum: General Help
---

### Post by shanali4 on 2009-08-15
I switched to Linux Kubuntu from Windows XP. When i opened file manager, it's not showing my partitions (C:, D:, E: etc.). When i click the root it shows many folders (bin, dev blah blah blah) and their are no partitions like in windows. Is my data lost, where are the partitions. PLZ HELP ME URGENTLY

---

### Post by Bachstelze on 2009-08-15
Edited to remove the large text. Please open up a terminal and paste the output of

```
sudo fdisk -l
```

---

### Post by zaphod777 on 2009-08-15
Also here is an article on the linux file system.
It explains what the various folders are for.

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by shanali4 on 2009-08-16
> **HymnToLife said:**
> Edited to remove the large text. Please open up a terminal and paste the output of

```
sudo fdisk -l
```

[SIZE=2]When i put that command it shows the following what is this i am not getting. plz help how to get back my files.

```
[sudo] password for shanali4:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe66be66b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9644    77465398+  83  Linux
/dev/sda2            9645        9729      682762+   5  Extended
/dev/sda5            9645        9729      682731   82  Linux swap / Solaris
```[/SIZE]

---

### Post by lisati on 2009-08-16
> **shanali4 said:**
> [SIZE=2]When i put that command it shows the following what is this i am not getting. plz help how to get back my files.

```
[sudo] password for shanali4:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe66be66b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9644    77465398+  83  Linux
/dev/sda2            9645        9729      682762+   5  Extended
/dev/sda5            9645        9729      682731   82  Linux swap / Solaris
```[/SIZE]

Ubuntu (and Linux in general) uses a different naming system for the partitions to Windows, so a serach for C:, D: etc will need a little thought to translate the names.

What I see in the output from fdisk is an Ubuntu installation, and no sign of the previous installation of Windows. 

When you installed Ubuntu, did you use the "Guided - use entire disk" option by any chance?

---

### Post by mrbiggbrain on 2009-08-16
seems like an off configure, there's an extended partition but only 3 partitions... abnormal, i dont see that much, what version are you running, it looks as though its

A - not seeing the NTFS drives,
B - They no longer exist (where wiped)

---

