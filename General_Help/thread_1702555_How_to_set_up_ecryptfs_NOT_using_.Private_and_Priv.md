---
title: "How to set up ecryptfs NOT using .Private and Private without root"
date: 2011-03-07
forum: General Help
---

### Post by narnie on 2011-03-07
I would like to set up my own ecryptfs on say ~/.mydir

I would like to be able to mount this without root.

I would like to know how I can set this up and implement it in daily use.

Something like

```
setup_ecryptfs_mount_without_root /home/username/.mydir /home/username/.mydir
```

do the setup of the encryptions, then unmount it with

```
unmount_ecryptfs_without_root /home/username/.mydir

```
Then I could reimplement it back up without having to run sudo with

```
mount_ecryptfs_without_root /home/username/.mydir /home/username/.mydir

```
I don't want to have to put anything in /etc/fstab (for one thing, so as not to alert anyone gaining access to the computer that "Hey, there is an encrypted system here. Hack it!"

I could tolerate having to set it up in the usual fashion with

```
sudo mount -t ecryptfs /home/username/.mydir /home/username/.mydir

```
I know this can be done because the ecryptfs-mount-private and ecryptfs-umount-private work in this fashion. I just want to use my own dirs rather than ~/.Private and ~/Private.

Thanks,
Narnie

---

