---
title: "How to restrict user access to automounted ntfs Windows partition?"
date: 2011-09-20
forum: General Help
---

### Post by ClyN3il on 2011-09-20
Sorry for being a little lazy, but my Googling so far has been fruitless...

I want my Windows partition to automatically mount on boot--I've done that--BUT I want it to be accessible ONLY to the primary user...the "guest" account I have set up for my students or whoever to screw around on my computer should not be able to access or modify the contents of my Windows partition. But I still want it to be automatically mounted and have complete access to it when I'm logged in on my account. How can I do this?

When I look at "permissions" in Nautilus for my Windows directories, it says only root can use it, even though I have complete read/write access to it. Which is fine--I set the fstab options that way intentionally--but I want only my primary account to have that access, not the secondary account.

Thanks!

---

### Post by Morbius1 on 2011-09-20
Post the output of fstab please:
```
cat /etc/fstab
```

---

### Post by ClyN3il on 2011-09-20
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=bbac80f5-58a7-4d92-8f33-3b03a130d787 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=365fa9c5-2f00-4ff8-b1bc-2d93b9fb1a59 none            swap    sw              0       0

#Manually added - automount windows partition LMR Sat 10 Sep 2011 08:18:53 PM KST
/dev/sda2    /media/OS    ntfs    user,fmask=0111,dmask=0000   0   0

Thanks!

---

### Post by madjr on 2011-09-20
i think you could also try **mount manager** in the software center

---

### Post by Morbius1 on 2011-09-20
Change this:
>  /dev/sda2    /media/OS    ntfs    user,fmask=0111,dmask=0000   0   0To this:
> /dev/sda2    /media/OS    ntfs defaults,uid=1000,[COLOR=Black]fmask=0177,dmask=0077[/COLOR]   0   0Then unmount the partition:
```
sudo umount /media/OS
```And run the following command to test for errors and mount the new partition settings:
```
sudo mount -a
```uid=1000 will make the owner you.
All those "7"'s in fmask and dmask because of their position will make it unavailable to anyone but you.

---

### Post by ClyN3il on 2011-09-20
> **Morbius1 said:**
> Change this:
To this:


Thanks! That accomplished exactly what I wanted to do!

---

