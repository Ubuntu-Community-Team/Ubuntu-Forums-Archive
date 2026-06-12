---
title: "Added new hdd, how do I add Trash folder?"
date: 2010-06-12
forum: General Help
---

### Post by bilodeau on 2010-06-12
I just got a new pc and installed ubuntu 9.10 on it.  I installed ubuntu on the primary drive and then added a partition on its second hdd for data storage.

Now I want Nautilus to treat this partition as its does my /home partition when I delete something.  Right now, if I right click on a file on the new partition and select 'Move to Trash', a window pops up with the message 'Cannot move file to trash, do you want to delete immediately?'

What do I do to get the desired behavior of the file being moved to the same Trash bin as files from my /home partition?

---

### Post by dcstar on 2010-06-12
> **bilodeau said:**
> I just got a new pc and installed ubuntu 9.10 on it.  I installed ubuntu on the primary drive and then added a partition on its second hdd for data storage.

Now I want Nautilus to treat this partition as its does my /home partition when I delete something.  Right now, if I right click on a file on the new partition and select 'Move to Trash', a window pops up with the message 'Cannot move file to trash, do you want to delete immediately?'

What do I do to get the desired behavior of the file being moved to the same Trash bin as files from my /home partition?

Format the partition as a Linux filesystem.

---

### Post by bilodeau on 2010-06-15
I _did_ format the drive as a linux file system (ext3) using gparted.  But the 'Move to Trash' option doesn't work on it.

---

### Post by WorMzy on 2010-06-15
EDIT: barking up the wrong tree.

---

### Post by ELD on 2010-06-15
> **bilodeau said:**
> I _did_ format the drive as a linux file system (ext3) using gparted.  But the 'Move to Trash' option doesn't work on it.

Sounds more like a bug, the move to trash option doesn't work for NTFS but should work fine for ext3?

---

### Post by WorMzy on 2010-06-15
Ignore my last post, it'd do the opposite of what you're after. Instead, create a folder in the partition's root directory called .trash-1000, and make sure that you *do* have write permissions to it.

---

### Post by dabl on 2010-06-15
When you format a partition, the partition obtains root privileges.  Normally it's best to leave it that way (i.e. let root own all hard drive partitions).  Make a directory on it for the user to use.

First, make a mount point and mount the filesystem:
```

sudo mkdir -p /mnt/MUSIC
```

```
sudo mount -t ext4 /dev/sdb1 /mnt/MUSIC
```

Now give your user permission to write in that directory:
```

sudo chown -R bilodeau /mnt/MUSIC
```

You can set this up to be mounted automatically in /etc/fstab.

Hope this helps.

---

### Post by bilodeau on 2010-06-15
I tried creating the .trash-1000 in the new partition's root directory, changing the permission to ugo+rwx, and then rebooting.  This didn't work.

I then did :

sudo chown -R paul.paul /data

and now the trash bin works as expected - plus no rebooting!  Hurray!

Thank you for the suggestions.  Has anyone else successfully enabled trash on other partitions without having to change the ownership of the entire secondary partition?

---

### Post by dabl on 2010-06-15
Trash can works correctly on 3 hard drives and 10 partitions, on my desktop system. Devices are owned by root, mount points by the user.

---

### Post by bilodeau on 2010-06-15
Okay, I did some messing around and discovered a few things.

When the 'Move to Trash' option started working on the second hard drive, a directory called .Trash-1000 that was owned by me and had 0700 access rights was made in the root directory.  The contents of this directory were the same as the ~/local/share/Trash - an expunged dir, an info dir, and a files dir.

If I copied this directory to my main directory on the new hard drive (one level down), and then removed the .Trash-1000 in the topmost level, 'Move to Trash' stopped working.  It only works if .Trash-1000 is in the uppermost directory of my data partition and is owned by me.

Now my question is: how do I empty and/or open this second trash bin?  Emptying is easy from the command line, but I want an icon I can press on my panel.  The default Trash icon only deals with the Trash on my /home partition.  I tried to add a custom launcher with the command 'rm /data/.Trash-1000/files/*', but this doesn't work.  No files are deleted.

---

### Post by bilodeau on 2010-06-22
An update for anyone who's interested:

After a couple of reboots, the trash now works correctly on my second hard drive.  I don't have to add a custom launcher or anything to the panel.  Just delete a file from the second data partition within Nautilus and it shows up in the Trash bin.

Yay!

---

