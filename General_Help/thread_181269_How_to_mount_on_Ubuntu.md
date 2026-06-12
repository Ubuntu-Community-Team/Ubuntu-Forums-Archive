---
title: "How to mount on Ubuntu?"
date: 2006-05-23
forum: General Help
---

### Post by wiwerion on 2006-05-23
I use SATA. I installed Ubuntu 5.10 in VMware workstation on xp home os. To mount I followed this guide...

Terminal
**sudo fdisk -l**  for partition control

Then;
[B]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
[/B]

Later
**sudo gedit /etc/fstab**

Adding to gEdit file;
**/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0**

After restart, on booting  **Mounting Local Filesystem failed ** is shown. 

Why I cant mount partitions?

---

### Post by olsonar on 2006-05-23
VMWare doesn't have direct access to your harddisk, and it can't be given it.  the best you're going to be able to do is set up file sharing between the host and guest OSes.

---

