---
title: "problem when chowning a mounted drive"
date: 2010-11-16
forum: General Help
---

### Post by barbedsaber on 2010-11-16
I have all my music on /dev/sda1

I have /dev/sda1 set to mount to /home/mynameistux/Music at boot
but it is all owned by root, so I can't add or delete any music
I tried running

```
sudo chown -R mynameistux /home/mynameistux/Music/
```
but I get
: Operation not permitted

what am I missing here? I would have thought that using sudo meant I would have the rights to change the permissions of the file?
I have also tried using sudo su, predictably getting the same result
this is doing my head in, any help would be appreciated.
cheers guys :)

---

### Post by sharath.puranik on 2010-11-16
I would suggest trying the following code in the terminal and DO NOT CLOSE THE TERMINAL till you finish doing your work.

```
sudo nautilus
```

Then do all the file modifications you want to. It worked for me but not too sure if it will work for you

---

### Post by barbedsaber on 2010-11-16
running xubuntu
thunar doesn't have the ability to do that, and I don't have nautilus.
do I really have to install an entire graphical program in order to perform a task that chown was designed for?

---

### Post by m_duck on 2010-11-16
If the disk is an NTFS or FAT formatted disk, *I don't think* those file system support Linux permissions and ownership so probably can't be changed with chown et al.

As far as I'm aware you must set the permissions and owner of the partitions at mount time.

---

### Post by sharath.puranik on 2010-11-16
> **barbedsaber said:**
> running xubuntu
thunar doesn't have the ability to do that, and I don't have nautilus.
do I really have to install an entire graphical program in order to perform a task that chown was designed for?

I didn't know that you were running xubuntu. The suggestion that I gave would start your file manager (in this case nautilus) in root mode which gives you complete access to all the files that are available on your system.
But that won't change the permissions of the drive that you wanted to do using chown.

It was a workaround and not an actual solution to your problem.

---

### Post by barbedsaber on 2010-11-16
> **m_duck said:**
> If the disk is an NTFS or FAT formatted disk, *I don't think* those file system support Linux permissions and ownership so probably can't be changed with chown et al.

As far as I'm aware you must set the permissions and owner of the partitions at mount time.

It's a FAT32 drive
well, that at least explains the problem.
is there anyway to fix the problem other than "take all the files off, format to ext4 and put them all back"

---

### Post by sharath.puranik on 2010-11-16
Try this [link]("https://help.ubuntu.com/community/MountingWindowsPartitions"). It gives you all the information needed to mount windows Drives.

---

### Post by deconstrained on 2010-11-16
Put 'uid=XXXX,gid=YYY' in the mount options (i.e. in /etc/fstab or after -o on the command line if mounted manually) where XXXX is your user ID and YYY any group ID you want. Anything else is unnecessary, cumbersome or even possibly dangerous.

---

### Post by barbedsaber on 2010-11-16
> **sharath.puranik said:**
> Try this [link]("https://help.ubuntu.com/community/MountingWindowsPartitions"). It gives you all the information needed to mount windows Drives.

thanks for the link, but it doesn't give any advice about owning drives, only for mounting them

---

### Post by m_duck on 2010-11-16
As I mentioned, you need to tell Ubuntu who owns the drive when its mounted due to the limitations of FAT drives with regards to Linux permissions.

Something like the following should mount from the command line giving 'mynameistux' ownership of the mounted drive, /dev/sda1:```
mount /dev/sda1 /home/mynameistux/Music -o uid=mynameistux,gid=users
```Or from fstab, to mount automatically at boot:```
/dev/sda1 /home/mynameistux vfat uid=mynameistux,gid=users 0 0
```

---

### Post by deconstrained on 2010-11-16
> **barbedsaber said:**
> thanks for the link, but it doesn't give any advice about owning drives, only for mounting them
That's the whole point. You specify who owns it when you mount it. An unmounted drive is just a special/device file in /dev, owned by root/the system, and cannot/should not be chowned.

Just do this, mmkay:
```
sudo mount -o uid=`id -u`,gid=`id -g`,fmask=0013 /dev/sda1 /home/mynameistux/Music
```

---

