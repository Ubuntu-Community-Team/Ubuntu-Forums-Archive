---
title: "Gparted makes new drive usable only to Root"
date: 2012-01-09
forum: General Help
---

### Post by MidnightbluRose on 2012-01-09
Hello all,

I went to make a new ext4 partition on an external drive today.  Used Gparted and now I can't put anything on the drive.  I checked the permissions, and it seems like only root has access to write on the drive.

I'm not sure what I did wrong.  I've used gparted plenty of times in the past, and it's never made drive need root permissions. 

I'm on 11.10

---

### Post by imachavel on 2012-01-09
can you log in as sudo su root user with your password? Can you delete the partition? Have you tried resetting the jumper on the main board to try and remove any hard drive locks? I don't want to give you a head ache. 

What did you install on what partition? This is all we can do from here is get more information before trying to assist you with your problem.

---

### Post by imachavel on 2012-01-09
sorry I didn't read this correctly. You made a new partition on a seperate external drive? And have already installed an OS to an internal drive?

Well, since you partitioned the new partition on an external drive, grub is probably looking for a new partition on the same drive where grub is found, installed on the first drive you install initial OS on. Delete the Operating system installed to the external drive from gparted. NOW, from the Main OS try and mount the drive, then install your .iso to the drive, no need to create a new partition. Just install to that drive. Then at boot select that drive from the boot menu, then you have two drives to boot from.

Sorry if I'm being general in my description but we know so little information from your post as it is. Good luck let me know if you work it out, why install seperate partitions from gparted to seperate drives? That sounds like it'd confuse the system to me.

---

### Post by oldfred on 2012-01-09
You need to set ownership & permissions.

sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sdb1 /mnt/data
#where sdb1 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 

And if you do not want to manually mount it each time you reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by nothingspecial on 2012-01-09
You run gparted as root so a new partition will be owned by root.

You need to change the ownership to your user like so

```
sudo chown -R $USER:$USER /media/[COLOR="Red"]blah[/COLOR]
```

You need to change [COLOR="Red"]blah[/COLOR] to whatever your new partition is mounted as in the media folder.

---

### Post by MidnightbluRose on 2012-01-09
> **nothingspecial said:**
> You run gparted as root so a new partition will be owned by root.

You need to change the ownership to your user like so

```
sudo chown -R $USER:$USER /media/[COLOR=Red]blah[/COLOR]
```You need to change [COLOR=Red]blah[/COLOR] to whatever your new partition is mounted as in the media folder.

Thank you, and it worked great!

All that makes sense, but like I've said I've partitioned at least 3 external drives with ext4 in Gparted in the past, and never had to change permissions from root to me before.

---

### Post by nothingspecial on 2012-01-10
No problem. :)

Next time you have a question and it is solved use the "Thread Tools" button at the top to mark it as solved please.

(I've done it for you this time ;))

---

