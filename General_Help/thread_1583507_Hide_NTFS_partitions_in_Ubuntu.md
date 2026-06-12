---
title: "Hide NTFS partitions in Ubuntu"
date: 2010-09-27
forum: General Help
---

### Post by matimont on 2010-09-27
Hi,

How can I hide NTFS partitions so that can't be mounted?
I noticed when I'm working on Ubuntu that I can delete files on my Windows NTFS partition, I think that's a risk..

Thanks,

---

### Post by srs5694 on 2010-09-27
You can't really hide partitions so that they absolutely 100% can't be mounted in Linux, short of physically removing the disks on which they reside. That said, I don't think you need that level of safety. I suspect you just don't want to accidentally click an icon and get into the NTFS partition. To do that, you can edit the /etc/fstab file. Add an entry like this for each partition you want hidden:

```

/dev/sda1  /mnt/hidden  ntfs-3g  noauto,ro  0 0

```

This configures the system to keep /dev/sda1 from being mounted automatically at boot time (the "noauto" part of the entry). It also sets it up so that it can be mounted manually at /mnt/hidden, but only as a read-only partition (the "ro" option). If you add the "users" option (as in "noauto,ro,users"), ordinary users (that is, you) will be able to mount the partition; but with this option missing, you'll need to use sudo to mount the partition. It's your choice how far you want to go with this -- you could leave out the "ro" and/or add "users", for instance.

---

### Post by matimont on 2010-09-28
I found a way to have Ubuntu ask for my password when someone tries to mount the partition. Thing is that in the Ubuntu 10.4 version it was not asking for my pass to mount partitions.
 
The reason I wanted this is because on the Windows partition I have sensitive data and other people in the house (mainly kids) use the ubuntu installation to play games over the internet, and may accidentally delete files on the windows partition, kids are curious..

---

### Post by Lateralis on 2010-09-28
You may want to read [this]("http://ubuntuforums.org/showthread.php?t=1305383&highlight=hide+NTFS") thread which describes a few ways to hide/make unmountable NTFS partitions.

---

### Post by srs5694 on 2010-09-28
Another option is to leave the NTFS partition permanently mounted, but set options on it such that only certain users can access it. An entry like this in /etc/fstab will be a start:

```

/dev/sdb5      /other/shared     ntfs-3g   uid=1000,gid=100,fmask=137,dmask=027  0 0

```

This mounts the NTFS partition /dev/sdb5 at /other/shared, giving ownership of all files to whoever has user ID (UID) 1000, setting the group of all files to group ID (GID) 100 (usually a group called "users"), and setting file permissions so that the owner can read and write all files, members of the group can read all files, and nobody else can access the files at all.

Assuming each user has his or her own account (which they should), this can be a good way to limit who can access Windows files. You can tweak the configuration, if you like; for instance, you can give read/write access to members of the group you specify, then be sure that only users who should have that sort of access belong to that group.

Incidentally, the issues brought up here are good reasons why a data and/or data transfer partition should be created, separate from the Windows boot partition. The boot partition can be configured to not mount at all, while the data transfer partition can be mounted such that some or all users can read or even write it. This configuration helps keep Windows safe from accidental damage, while still maintaining the flexibility of data transfer between OSes.

---

### Post by mycelo on 2010-10-04
> **srs5694 said:**
> ```

/dev/sda1  /mnt/hidden  ntfs-3g  noauto,ro  0 0

```Well that not only looks neat, it seems like a clean, simple and effective solution.

I'd also like to add that Vista/7 system or boot partitions must NEVER be mounted R/W on Linux. It does read and write NTFS partitions quite well and mostly free of troubles. BUT it somewhat wipes the System Restore data, which, as far as I know, is stored in the free space. Windows preserve it until it needs more room, but Linux won't, since it's beyond NTFS specifications.

I always have a generic NTFS partition somewhere where I keep the files I want being accessed by both OSes.

---

