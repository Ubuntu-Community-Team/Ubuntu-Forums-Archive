---
title: "need system backup... but wait. there's stips"
date: 2010-10-22
forum: General Help
---

### Post by jhongomz on 2010-10-22
Okay, I am looking for a backup program to backup my system only.  As in, I want an image that I can reinstall in case of system failure.  I only want the system along with programs and settings but without my media directories.  So I would like to have something that allows a system backup minus folder a and folder w and folder x.  A system that would be easy to image back. 

I feel that it is out there and I am just missing for whatever reason.

Thanks for any and all help.

---

### Post by HermanAB on 2010-10-22
rsync

---

### Post by coffeecat on 2010-10-22
> **jhongomz said:**
> I feel that it is out there and I am just missing for whatever reason.

There is. The simple tar command from the terminal will do the job. I've been using it to backup, restore and clone whole systems for years. You can include the --exclude=FILES/FOLDERS option to do just that. A couple of caveats:

Always tar from "outside" the system. It's best to use a live CD or a Linux install on another partition if you have one.

When you restore, if you have reformatted the destinaton partition, you will need to edit /etc/fstab to account for the changed UUIDs and also do something about repairing grub's UUID references. And restore grub stage 1 to the mbr if need be.

What I do to create a tar.gz image (you can use tar.bz2, but it's slower) is to mount the partition to be imaged, cd to it and...

```
sudo tar -czvf /path/to/storage/medium/filename.tgz *
```Of course that doesn't exclude anything - it's a basic wrap everything up and backup option. But if you're worried about the mounted stuff in /media, that won't matter anyway, because you are outslde the system and nothing is mounted to the system's /media.

Some people may tell you to --exclude all the virtual folders such as /proc and /dev. Complete waste of time and typing effort, I can assure you.

---

### Post by Megaptera on 2010-10-22
Don't overlook CD/DVD through Remastersys. Guide from here:

[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by xib.be on 2010-10-22
rsync -rltv --progress file1 file2 file3 file4  backup/
or simply 
cp -rp file1 file2 ... backup/

if some folders are confidential, use ecryptfs-utils
sudo mount -t ecryptfs secret secret
your-pass-phrase
aes
32

then rsync in it

finaly umount secret

so you can stock on an external device without caring ;)

---

