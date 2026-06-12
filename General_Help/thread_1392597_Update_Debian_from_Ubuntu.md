---
title: "Update Debian from Ubuntu"
date: 2010-01-28
forum: General Help
---

### Post by TheForkOfJustice on 2010-01-28
My system has Ubuntu and Debian (Squeeze) on it.

I don't want to have to boot up Debian in order to get the recent updates.

Is there a way to do this from Ubuntu?

---

### Post by sisco311 on 2010-01-28
> **TheForkOfJustice said:**
> My system has Ubuntu and Debian (Squeeze) on it.

I don't want to have to boot up Debian in order to get the recent updates.

Is there a way to do this from Ubuntu?

Yes you can chroot in the Debian installation:

Mount the root partition
```
sudo mkdir /mnt/debian
sudo mount /dev/sda1 /mnt/debian
```
replace /dev/sda1 with the correct device.

EDIT: If you have separate /boot, /home, /usr... partitions, mount them as well under /mnt/debian/boot, /mnt/debian/home... 

Mount the virtual filesystems:
```
sudo mount --bind /dev/ /mnt/debian/dev
sudo mount --bind /dev/pts /mnt/debian/dev/pts
sudo mount -t proc none /mnt/debian/proc
sudo mount -t sysfs none /mnt/debian/sys

```

Setup the network:
```
sudo mount -o bind /etc/resolv.conf /mnt/debian/etc/resolv.conf
```

Chroot in debian:
```
sudo chroot /mnt/debian
```
Note1: you are logged in as root, you can use su or sudo to log in as a different user.
Note2:to launch GUI apps as a non-root user, run:
```
xhost +
```in Ubuntu.

Update the system:
```
apt-get update
apt-get upgrade
```

Or login as an admin user and run update manager:
```
su - username
update-manager
```  

Press Ctrl+d to exit from the chroot.

---

### Post by TheForkOfJustice on 2010-01-29
Thanks for all of this but I hit a snag.  I already had some chroots set up and chroot is behaving odd now when I get to this part:

> **sisco311 said:**
> 
Chroot in debian:
```
sudo chroot /mnt/debian
```


The error looks like this:

> 
mackinal@mackinal:~$ sudo chroot /mnt/debian
chroot: cannot run command `/bin/bash': Exec format error


I'm using amd64 versions of Karmic and Squeeze.

---

