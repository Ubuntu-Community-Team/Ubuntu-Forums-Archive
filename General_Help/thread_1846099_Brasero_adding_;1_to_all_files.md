---
title: "Brasero adding ;1 to all files ?"
date: 2011-09-18
forum: General Help
---

### Post by zami on 2011-09-18
I'm trying to make an .iso from my Age of Empires disc, using Brasero.

For some reason, it's adding ;1 to every, single, file.  The directories look good, but the files all have to be renamed for this .iso to be useful.

Any clues why this is happening or how to make it STOP happening?


Process:
insert AOE disk
start Brasero
select "Disc Copy"
disc to copy = AOE, disc to write to = Image File, Properties = ISO9660image
Create Image

Result:
brasero.iso
full of files amended with ;1 at the end

I've had Brasero check the integrity of the disk, and it thinks it's fine.  I'm not getting any errors, just that awful renaming issue.

This has happened with another disk in the past, and I went through and removed the ;1 from all the files but that's just a huge hassle, and surely there is a way to just not have those extra characters glued on?

---

### Post by zami on 2011-09-18
I found a bug report on the same problem, but there was never any follow up on it.
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/212410](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/212410)

---

### Post by srs5694 on 2011-09-18
A semicolon and a number are a standard part of ISO-9660 filenames. Linux, like most OSes, hides those from view when a disc is mounted normally. You don't say how you were reading the image file you created, but it's possible that the method you used did *not* hide those filename features. I recommend you try this, from a Terminal window:

```

sudo mount -o loop brasero.iso /mnt
ls /mnt
sudo umount /mnt

```

Change the filename as necessary. If the files you see in /mnt lack the semicolons and numbers, then the image is fine, and you just need another way to mount the disc, such as the mount command I just specified. You can do whatever you like with the mounted image file, and use "umount" to unmount it when you're done with it.

---

