---
title: "How to recover Ubuntu files on hard drive from Live CD"
date: 2011-05-25
forum: General Help
---

### Post by SirGonzo420 on 2011-05-25
A recent update messed up my Ubuntu (actually Xubuntu) laptop, and so I want to recover a few important files off of it before reinstalling the OS.

I cannot boot into Ubuntu on my hard drive, so I put in one of my Live CDs, but couldn't figure out how to get the files from my hard drive.

I googled the problem, but all the solutions talked about recovering Windows files with a Live CD.

I need to recover my files that were in Ubuntu!



I am not very linux savvy, although I've been using Ubuntu and Xubuntu for a few years now. heh...

Anybody wanna help?

---

### Post by satanselbow on 2011-05-25
Boot the live CD (obviously)

Mount the partition you want to recover from
Mount the partition you want to recover to

open terminal

```

gksu nautilus

```

copy away my friend ;)

---

### Post by seawolf167 on 2011-05-25
As said above, it is pretty easy and straightforward.

Burn the Ubuntu LiveCD, boot off it, then select the "Try Ubuntu without Installing" option. Once you see the desktop, you can mount your disk via the GUI by going to Places -> Filesystem XYZ (where Filesystem XYZ is your Ubuntu partition). After it is mounted you can drag & drop your files to your external harddrive.

If you need to copy folders/files owned by root, or need higher permissions, as stated above, type

```
gksu nautilus
```to open your file manager with root permissions, then copy the items you need.

---

### Post by SirGonzo420 on 2011-05-25
> **satanselbow said:**
> Boot the live CD (obviously)

Mount the partition you want to recover from
Mount the partition you want to recover to

open terminal

```

gksu nautilus

```copy away my friend ;)

I see "73.1 GB Volume" under "File System", but when I try to mount it it says it cannot mount volume....

---

### Post by seawolf167 on 2011-05-25
Is it already mounted?

You can type 

```
mount
```

to see mounted partitions, and 

```
sudo fdisk -l
```

to see available partitions on your disks (i.e. to use with the *mount* command).

If you are still having problems mounting your disks to copy off files, please run the two above commands and copy/paste them into CODE tags in your reply.

---

