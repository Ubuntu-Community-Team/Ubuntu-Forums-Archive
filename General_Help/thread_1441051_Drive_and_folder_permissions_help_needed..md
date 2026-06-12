---
title: "Drive and folder permissions help needed."
date: 2010-03-28
forum: General Help
---

### Post by schlitz100 on 2010-03-28
I am very new to Ubuntu. I installed 9.10 on my home theatre PC last night. I have 3 NTFS partitions that hold my media that I am in the process of changing to ext4. I emptied the first partition last night then used gparted to format to ext4, then started having issues with permissions.

First I couldn't write to the drive at all, getting a permission errors which I figured out with google how to load nautilus as an admin(?) to change the user to myself. Then I copied back all of the files. To my annoyance every folder and sub folder that I copied to this drive I again lost permission to use and had to change the user manually for every folder which was a PITA to say the least.

So, how do I make it so every folder I copy to this drive I don't lose permissions? 

Is there any way I can format the next two drives differently so this same issue doesn't occur two more times?

Thanks

---

### Post by oldfred on 2010-03-28
It is usually how you mount them or permanently mount them via fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

You usually have to set ownership and permissions. If you have a data partition:

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions.

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name, -R is recursive so all lower levels are changed. 777 is very permissive read, write & execute for everyone, adjust if not what you want.

---

