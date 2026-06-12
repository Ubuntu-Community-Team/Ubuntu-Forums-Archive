---
title: "Migrating all FS to new storage"
date: 2010-08-15
forum: General Help
---

### Post by Fludizz on 2010-08-15
Ok, so I'm in the process of duplicating all the data from my existing filesystems to a new storage solution. I know it is not recommended to do so but this will be a *lot* faster then having to reinstall and reconfiguring the system from scratch...

I've synchronized the filesystems using rsync, used the following command line for that:
```
rsync --recursive --acls --xattrs --delete --force --one-file-system --links --perms --owner --group --stats --specials --devices --human-readable / /mnt/sde1
rsync --recursive --acls --xattrs --delete --force --one-file-system --links --perms --owner --group --stats --specials --devices --human-readable /var/ /mnt/sde3
```

Currently "/" is on /dev/md0, swap on /dev/md1 and "/var/" is on /dev/md2. The target is to have "/" on what is now identiefied as /dev/sde1, swap would go to /dev/sde2 and "/var/" to /dev/sde3. 

To make sure all data is mirrored properly, the next step is to boot into a live system and rerun rsync to copy any previously locked/altered files to the new storage. After moving this, I know I have to edit /etc/fstab on the new storage to make it match the proper UID for the drives. I also have to update grub and install grub into MBR of the new storage.

Anything else I need to keep in mind to be able to boot the system from the new storage?

---

### Post by Fludizz on 2010-08-16
Ok, I did this yesterday. Booted into a Ubuntu Live CD and executed the rsync commands. After the rsync completed, I dismounted both drives to make sure they are no longer in use.

Next step was mounting /dev/sde1 (the new root) and mounting /dev/sde3 on /mnt/sde1/var (and offcourse proc and dev fs) and chroot to the new root:
```
mount -t ext3 /dev/sde1 /mnt/sde1
mount -t jfs /dev/sde3 /mnt/sde1/var
mount -t none proc /mnt/sde1/proc
mount -o bind /dev /mnt/sde1/dev
chroot /mnt/sde1 /bin/bash
```

After this I edited fstab to contain the new UUID's for the new storage, edited menu.lst and changed the kopt= line to /dev/sda1 (yes, due to the upgrade from 8.04 to 10.04, it is using /boot/grub/menu.lst and not /etc/default/grub).

At this point I shut down the machine, removed the old storage and placed the new storage on it's permanent port. Booted into the live CD again and performed the same steps again to mount it (except now it has become /dev/sda instead of /dev/sde). After chrooting back into the filesystem, I installed grub into the mbr and rebooted the system again: 

The system booted into the new storage and no failures observed during boot :)

---

### Post by didac on 2010-08-16
Thank you! I was about to do the same, changing hard disks, but using the directions in the old HOWTO Hard-Disk-Upgrade, cp -ax Your solution is neater.

---

### Post by KeyserSoze93 on 2010-08-17
great, glad it worked. i wrote a similar piece about cloning debian, which could probably be applied also to Ubuntu:

[http://tpn.lowtech.org/tips/clonedeb.txt](http://tpn.lowtech.org/tips/clonedeb.txt)

---

