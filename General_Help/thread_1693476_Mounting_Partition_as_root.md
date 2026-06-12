---
title: "Mounting Partition as root?"
date: 2011-02-22
forum: General Help
---

### Post by buntuser2 on 2011-02-22
I created a 20gb encrypted partition on my HD. I only want the super user or "root" user to be able to mount this partition.  Right now it is not, so I can't write to the partition unless I mount it as root or super user.  I don't want to change ownership. I want to have to mount it as root every time I access this partition.  Again, I do not want to change ownership.  Is there a command for this? I tried the mount command :/

---

### Post by Old *ix Geek on 2011-02-22
Unless there's an fstab entry allowing other users to mount/unmount a drive, only root can do it. What's in your /etc/fstab regarding this drive?

---

### Post by doas777 on 2011-02-22
well, the mount command itself requires sudo (root), but if you use a userspace mount utility to mount the drive, then ownership is the only mechanism that can be relied upon. 

you can't really control the means used to mount a drive, since it can be plugged in to any given system. all you can really do is control what gets done with the data after mounting. even ownership won;t secure your data if it's in someone elses machine. at that point, encryption is all you can really do.

---

### Post by srs5694 on 2011-02-23
[quote=buntuser2]I created a 20gb encrypted partition on my HD. I only want the super  user or "root" user to be able to mount this partition.  Right now it is  not, so I can't write to the partition unless I mount it as root or  super user.[/quote]

It's unclear to me precisely what the problem is. First you say that you only want root to be able to mount the partition, then you say that the problem is that you can't write to the partition unless you mount it as root. This problem seems to fly in the face of your stated goal.

If you want to restrict access to the partition so that only root may write to it, simple permissions settings might do the trick, as in:

```

sudo chown root:root /mnt/point
sudo chmod 0700 /mnt/point

```

These commands give ownership of /mnt/point (change this as necessary) to root and gives only root the ability to write to the filesystem. If you mean you want some user other than root to be able to access the filesystem, then changing the owner and/or permissions will do the trick.

If your problem is that the partition is being mounted by a file manager and you don't want it to be mounted in this way, you can create an /etc/fstab entry, thus:

```

/dev/sda6    /mnt/point   ext4   noauto   0 2

```

This example enables root, and only root, to mount the /dev/sda6 partition. It will mount at /mnt/point by default (for instance, by typing "sudo mount /mnt/point"), but another mount point can be specified (for instance, by typing "suo mount /dev/sda6 /mnt/someotherpoint"). Of course, the mount point must exist in either case. You may need to add options to "noauto" for your specific case. (I'm not sure offhand what you'd need for an encrypted filesystem, for instance.)

Please post again with clarifications if I'm way off base about what you want to do.

---

