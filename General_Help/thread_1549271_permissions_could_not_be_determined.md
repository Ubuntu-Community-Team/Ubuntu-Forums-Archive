---
title: "permissions could not be determined"
date: 2010-08-09
forum: General Help
---

### Post by peterthewolf on 2010-08-09
I am trying to use a second sata 3.5 HD and at other times a USB 2.5 HD.
Both prove a pain to use because Ubuntu tells me their permissions can not be be determined.
They have only been partitioned to ext2 on Ubuntu.
This happens on 9.04 10.04 and 10.10

I have searched the web about this found many answers which just do not work.

This is such a basic problem the answer should be easy to find So please can somebody cure my problem.

Thanks in advance.

---

### Post by dino99 on 2010-08-09
there is an easy tool to deal with partitions and devices: mountmanager, set your prefs into "system admin mountmanager (install it with synaptic)

---

### Post by ajgreeny on 2010-08-09
Mostly external disks are formatted to fat32, so permissions do not present a problem.  You have formatted to ext2, however, so the folder made automatically in /media when the disk is inserted will need to be owned by yourself as user.  I am not certain how this can be made to happen, but wonder if perhaps you need to edit /etc/fstab and make permanent mount points in /media or even /mnt.  I am not sure what happens if you attach a usb drive that has a permanent mount point in /media, as normally a folder will be made by the system when the disk is attached.  Sorry if that is just confusing but it may give you more possible searches to make.

I have just checked my own system permissions on an external drive I use for backups, an Iomega 250GB disk, which has a single partition which mounts at /media/Iomega, and that folder /media/Iomega, belongs to me as user, as do the subfolders in the folder, so  maybe you only need to chown the folders to yours with ```
sudo chown user:user /media/foldername
```I'm pretty sure that's what I did.

---

