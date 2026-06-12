---
title: "Getting permission to my own drive"
date: 2006-02-21
forum: General Help
---

### Post by Fred Doolie on 2006-02-21
I have an external USB drive that I'd like to partition, format and use. The problem is permissions.

If I do it in Winblows (Partition Magic or Win Drive Manager) it comes up read-only in Ubuntu.

cfdisk /dev/sda tells me I don't have permission to change the drive.

sudo cfdisk /dev/sda works but then I have to be root to write to it afterwards. I want to R/W it as my personal user account.

On that same subject, anything I drag and drop from the Windows partiton gets a lock on the icon and I can't delete/edit the files and folders except as root. What a pain. Why is Ubuntu locking my files and drives?

Thanks

---

### Post by free0n on 2006-02-21
Hey,

I'm kinda curious about this as I have this happening with my usb device. What does it tell you when you run this in console then plug in/out your usb device?

 tail -s 3 -f /var/log/messages


Well i got mine to work I had to edit the /etc/fstab and add
```

/dev/sda        /media/USBdrive vfat    rw,user,umask=0      0       0

```

As far as the partition goes mine uses fat and it works fine on both ubuntu and windows. Good luck :)

---

### Post by Fred Doolie on 2006-02-21
Problem 1/2 solved.

Used gParted to redo the drive. Had to enter password to use it.
Noticed after logging in and out a few times changing user names that when *I* logged in the Fat32 partiton auto mounted but not the Ext3. When root logged in both partitions auto mounted. Also *I* was prevented from writing to the Ext3 partition but root was not. Got an idea and checked the "Properties" option on the partitions (from Gnome desktop). Aha! They CAN be changed but the owner has to do it. So I logged on as root and gave "Everyone" R/W access. Now *I* can access both partitons and they automount. 

Now....why are my dragged files being locked?

---

### Post by alan.mckinnon on 2006-02-22
[QUOTE=Fred Doolie]Problem 1/2 solved.

Used gParted to redo the drive. Had to enter password to use it.
Noticed after logging in and out a few times changing user names that when *I* logged in the Fat32 partiton auto mounted but not the Ext3. When root logged in both partitions auto mounted. Also *I* was prevented from writing to the Ext3 partition but root was not. Got an idea and checked the "Properties" option on the partitions (from Gnome desktop). Aha! They CAN be changed but the owner has to do it. So I logged on as root and gave "Everyone" R/W access. Now *I* can access both partitons and they automount. 

Now....why are my dragged files being locked?[/QUOTE]

A FAT drive has no concept of permissions or owners - it only has files on it. Linux *always* has owners and permissions attached to ALL files, so in the case of FAT drives it has to use default permissions when the drive is mounted. This is done in /etc/fstab.

The easiest way is to include 'umask=0' in the mount options. This will use permissions 777 for all files and directories (read/write/execute for owner, group and everyone else). This is the permissions that Windows uses so it probably will work for you.

The permissions used on a FAT drive depend only on what /etc/fstab says. You can try change one file as root but it probably won't work, and will definitely not remember the change the next time you mount it.

The permissions for ext3 depend on /etc/fstab settings, and on the current user's umask - 0002 is a good start value but you should customize it to suit your needs.

All the answers you need are in
man mount
man 5 /etc/fstab
man umask

---

