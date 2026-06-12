---
title: "Automount my second hard drive"
date: 2011-11-10
forum: General Help
---

### Post by TheNEScollector on 2011-11-10
I'm trying to move completely over to Linux from MS Windows. Everything has been fine so far with only a couple of bumps along the way. However, I just moved my second hard drive into my new computer running Ubuntu. My second hard drive has all of my music from my old, Windows XP, computer on it and nothing else. After playing with it for a while, I got it in and it works great, but it doesn't mount on start up, and I would like it to. I really don't know much about the mounting of drives in Ubuntu, so I really need some help with this. Thanks for all of your help!

---

### Post by DapperMe17 on 2011-11-10
If that drive is formatted to NTFS, you can easily install the ntfs-config GUI and set it to mount the drive at boot time.

---

### Post by oldfred on 2011-11-11
I have not had good luck with any of the gui tools. Although they try to automate the process of creating a mount point and adding an entry to fstab with supposedly correct parameters.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Good overall guides:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)


Manual mount:
sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

Typical fstab entries but you have to use your UUID, I think I have just used defaults and it works, each example already has the mount point created:
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
```
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,windows_names,umask=000 0 0
```Another example but it is better to use UUIDs
What this will do is mount the partition with owner = root but with read / write permissions ( umask=007 ) granted to all local login users ( gid=46 ).
```
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0

```mounted an ntfs partition with me (uid=1000) as owner and with permissions for me and all local login users ( gid=46 ) to read / write and with no permissions for anyone else (umask=007).

---

