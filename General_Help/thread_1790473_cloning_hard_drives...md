---
title: "cloning hard drives.."
date: 2011-06-25
forum: General Help
---

### Post by Zerocool Djx on 2011-06-25
What is the best software to do this?

Basically, I have a 250 GB HD and a 2 TB external hd. I would like to make a full copy of the system as a raw image and basically have a one button click to copy it to the main if anything should happen. I have a ton of programs and I am tired of reinstalling everything after a snafu. It usually takes a week to reinstall everything with settings the way I like.

---

### Post by martinr on 2011-06-25
Here's how to make a raw copy of your entire drive.

Preliminary:

1. Check that your backup/destination drive can hold a 250GB big file.
2. Boot with a linux live CD or rescue disk and do not mount the source drive you want to copy.
3. Find out the device name of the drive that you want to copy (for example: /dev/sda ).
4. Mount the drive that you want to write the backup image on.
5. Determine the location where you want to store the raw copy. (for example: /media/backupdrive/ )

Make the raw copy:

6. Become root and make a raw copy of your source drive to destination drive.
```

$ dd if=/dev/sda of=/media/backupdrive/backup-sda.bin

```

Restoring:

7. To restore a disk image you previously made do the following.
```

$ dd if=/media/backupdrive/backup-sda.bin of=/dev/sda

```

These are powerful commands and remember:
With great power comes great responsibility. :)

---

### Post by jmszr on 2011-06-25
Zerocool Djx,

There also is Clonezilla: [http://clonezilla.org/](http://clonezilla.org/) .

I've used it and it works quite well, easy to use and efficient.

Edit: Sorry, I missed the "raw image" part of your post-Clonezilla doesn't clone the unused blocks. I plead no coffee yet this morning.

---

