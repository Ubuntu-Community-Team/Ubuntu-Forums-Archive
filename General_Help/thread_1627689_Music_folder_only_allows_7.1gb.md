---
title: "Music folder only allows 7.1gb"
date: 2010-11-21
forum: General Help
---

### Post by ingrown.potato on 2010-11-21
I'm transferring all my music (about 25gb) from windows to ubuntu. When I try and copy everything from my external hard drive it gives me an error saying there is not enough space. Is there a way to allocate more memory for my music folder?

---

### Post by sohlinux on 2010-11-21
you cant allocate memory for your music files, you need disk space

what size is your hard drive?

by chance do you have any free partitions on the ubuntu drive? you can look in the menu in system - administration - disk utility, it will show you the drive. if you have a free partition you can mount it and make a symbolic link or you can resize the partition but first ascertain how your drive is being used, does it have windows as a dual boot?

---

### Post by ingrown.potato on 2010-11-21
I have a 750gb hard drive. I just partitioned my hard drive to install ubuntu. I made 367gb for NTFS  (because it said that was the minimal required) 30gb for ubuntu, 10 for swap, 10 for a seperate home ext3, and the rest in a FAT-32 (which when i go to teh disk manager you told me about it is listed as unknown). I was told the FAT-32 acts as a shared folder.

---

### Post by Verbeck on 2010-11-21
> **ingrown.potato said:**
> 10 for a seperate home ext3

that's where your music folder is :-?

---

### Post by oldfred on 2010-11-21
Never heard of 367GB as minimum for windows, more like 20GB for XP and 30GB for Vista/7.

Also you should use NTFS for a shared folder. Any file over 4GB in a FAT partition will be truncated and you destroy file.

---

### Post by sohlinux on 2010-11-21
> **ingrown.potato said:**
> I have a 750gb hard drive. I just partitioned my hard drive to install ubuntu. I made 367gb for NTFS  (because it said that was the minimal required) 30gb for ubuntu, 10 for swap, 10 for a seperate home ext3, and the rest in a FAT-32 (which when i go to teh disk manager you told me about it is listed as unknown). I was told the FAT-32 acts as a shared folder.

if you already have the music in your windows partition you don't need to copy it to the ubuntu partition - just make a link to it.

you can create a link by just drag and drop in the file manager or use ln command in the terminal

if you haven't already you may want to mount the windows partition at boot which can be done with software like mountmanager but be careful and make a backup of /etc/fstab first.

---

### Post by ingrown.potato on 2010-11-22
> **oldfred said:**
> Never heard of 367GB as minimum for windows, more like 20GB for XP and 30GB for Vista/7.

Also you should use NTFS for a shared folder. Any file over 4GB in a FAT partition will be truncated and you destroy file.

How could I use ntfs as a shared? I thought that you could only use fat32

---

### Post by ingrown.potato on 2010-11-22
> **sohlinux said:**
> if you already have the music in your windows partition you don't need to copy it to the ubuntu partition - just make a link to it.

you can create a link by just drag and drop in the file manager or use ln command in the terminal

if you haven't already you may want to mount the windows partition at boot which can be done with software like mountmanager but be careful and make a backup of /etc/fstab first.

How could I do that?

---

### Post by eriqjaffe on 2010-11-22
If you want to auto-mount the drive at bootup...

In the terminal, find the UUID of the drive(s) you want to mount:

```
$ sudo blkid
```

That'll generate a list of what drives you've got.  Mine looks like this:

```
eriq@eriq-ubuntu:~$ sudo blkid
/dev/sda1: UUID="00000000458D9A71" LABEL="Windows" TYPE="ntfs" 
/dev/sdb1: UUID="a1f1702d-5349-4457-b116-7e7fd57e8916" TYPE="ext3" 
/dev/sdb2: UUID="7b17b40f-bd72-43d5-a97d-21fc3a916736" TYPE="swap" 
/dev/sdb3: UUID="1211c9d0-3fc2-479a-b3b8-9c884500be76" TYPE="ext3" 
/dev/sdc1: UUID="4110E0A85F16A4B6" LABEL="Music" TYPE="ntfs" 
/dev/sdd1: UUID="3C2D3C9F491B1A16" LABEL="D:" TYPE="ntfs" 
/dev/sdd2: UUID="3429C5520E412D92" LABEL="E:" TYPE="ntfs"
```

So I know my Music drive is located at /dev/sdc1, it's UUID is 4110E0A85F16A4B6, and it's formatted NTFS.  If you need additional assistance in figuring out which drive is which, you can enter "sudo fdisk -l" in the terminal for greater detail.

Once you've identified the UUID of the drive, you can mount it automatically by editing /etc/fstab (make a copy of it first):

```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

Create a mount point (sudo mkdir /media/Music), and add a line similar to this:

```
/dev/disk/by-uuid/4110E0A85F16A4B6 /media/Music ntfs-3g defaults,uid=1000,locale=en_US.UTF-8 0 0 
```

You can save /etc/fstab, and then run "sudo mount -a" from the terminal to mount the "new" volume.  On subsequent reboots, it'll mount automatically.  Hopefully, that makes enough sense.

---

