---
title: "Cannot get write access to samba share"
date: 2011-11-24
forum: General Help
---

### Post by apdobaj on 2011-11-24
I'm trying to set up a NAS system for my home network. My laptop is running Ubuntu 11.10 and desktop is running vista. I have a USB hard drive attached to my Linksys E1550 router to act as the NAS. I've been able to edit fstab to mount the NAS partitions to a folder, but no matter what I do I cannot get the mount point to be writable. It doesn't matter whether I use fstab or use the smbmount command from the terminal. Here is the command line I've been using:
sudo smbmount -w //*router_name*/*share_name* /mnt/smb_mnt_engineering -o ip=*router_IP*,rw,user=*username*,password=*password*,user,umount=0000,auto

When I use Nautilus to browse the network I can mount the NAS shares and they are rw just fine. I need the mount points so I can use a sync utility. Thanks for the help.

---

### Post by z84976 on 2011-11-24
When it's mounted in Nautilus, take a look at what's in mtab and match up your permissions with that in fstab maybe...

---

### Post by apdobaj on 2011-11-29
Great thought, but I cannot see any difference in the mtab file before mounting and after. Note that by "mounting" the NAS partition in Nautilus I mean going to the "Network" section of the sidebar and double clicking "Browse Network" until I drill down to the folder on the NAS that I'm trying to access. This folder then shows in the sidebar as *folder_name* on *router_name* with the up-arrow mounted icon shown to the right.

---

### Post by apdobaj on 2011-12-02
Figured it out. The fstab line is: //router_name/share_folder   /mnt/mount_name    cifs    ip=192.168.1.1,rw,user=windows_workgroup/user_name%password,file_mode=0777,dir_mode=0777,uid=linux_user  0  0

Big trick is getting the ownership correct with the uid parameter.

---

