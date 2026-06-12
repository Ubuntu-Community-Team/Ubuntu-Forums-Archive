---
title: "/home move failed"
date: 2011-04-04
forum: General Help
---

### Post by yuler on 2011-04-04
I wanted to move /home, move didn't work, so I reverted.  Here's what I did.

```
sudo blkid
```/dev/sda8: LABEL="general" UUID="041afce9-950a-4a68-bb76-88110b3e3f5b" TYPE="ext4" 

```
rsync -ax /home /media/general/home/
```Then I added UUID of partition "general" to fstab.newhome

/etc/fstab
UUID=ef1abebf-8af9-4642-acc8-502286785770 swap swap sw 0 0
UUID=9c828ded-432e-4028-b090-0659ac21aa19 / ext4 defaults 0 1
UUID=465C89C95C89B3E9 /media/160gb ntfs-3g noatime,dirsync,sync,umask=000 0 0

/etc/fstab.newhome
UUID=ef1abebf-8af9-4642-acc8-502286785770 swap swap sw 0 0
UUID=9c828ded-432e-4028-b090-0659ac21aa19 / ext4 defaults 0 1
UUID=465C89C95C89B3E9 /media/160gb ntfs-3g noatime,dirsync,sync,umask=000 0 0
UUID=041afce9-950a-4a68-bb76-88110b3e3f5b /home ext4 nodev,nosuid 0 2

1) copied fstab to fstab.bak
2) booted to recovery mode/root
3) copied fstab.newhome to fstab
4) booted to normal, got new desktop and forgotten Empathy settings

I assume the the remapped home did not take or the map took, but the rsync copy didn't grab everything.  What did I do wrong?

Booted back to recovery/root, copied fstab.bak fstab.

---

### Post by oldfred on 2011-04-05
Did you follow all the steps.

But I think this one is missing a create mount command:
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

This one use cpio instead of rsync, I prefer rsync. But instructions are otherwise the same.
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Quick instructions (missing required fstab entries)

#Format new partition:
sudo mkfs -t ext4 /dev/sdb1
sudo mkdir /mnt/newhome
sudo mount /dev/sdb1 /mnt/newhome
sudo cd /home
#copy everything in /fred (.) to newhome -a preseverses ownership & permissions
sudo rsync -rauvP . /mnt/newhome

---

### Post by yuler on 2011-04-05
Hi again, Oldfred.  Those were the two main sources I used, although I didn't follow it exactly.  While checking my work, I noticed I used

```
rsync -av /home /media/general/home
```[FONT=monospace]

When [/FONT]PartitioningHomeMoving said to use:

```
rsync -ax /home /media/general/home/
```[FONT=monospace]

[/FONT]So I did, but aborted.  Now I can't delete the /media/general/home folder because it and most it's ancestors is owned by root.   I don't think I can't login to the GUI to become root, so using the CLI as root to remove those folders one by one is apparently my next task.

---

### Post by oldfred on 2011-04-05
You can become sudo in Nautilus but have to be extremely careful as root you can cause damage. You can and should be setting permissions & ownership of your /home partitions to you anyway.

gksudo nautilus

What ever you newhome is should have this as the ownership & permissions.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 600 $HOME/.ICEauthority

---

