---
title: "Cannot write to External USB drive"
date: 2009-07-27
forum: General Help
---

### Post by MacDuff on 2009-07-27
My apologies for adding to the forum clutter but I have run out of ideas.

I have a 600Gb external hard drive that was formatted FAT32 and of course would not accept files larger than 4Mb so I re-formatted it to EXT3.

Now Ubuntu will mount the drive automatically when it is plugged in and I can see the only directory on it (Trash) but cannot add directories.

The option to "add" in Nautilus is greyed out.

I have changed permissions but that did not work and I cannot change the owner so obviously I am doing something wrong.

Does anyone have a simple solution to this problem?

---

### Post by DaithiF on 2009-07-27
Hi,
when you formatted to EXT3, you probably did this as the root user using sudo, or via a graphical application launched via gksudo.  The result is that the files on this drive are owned by the root user, and your own username doesn't have write access.

You can fix this by changing the owner to yourself.

Open a terminal.
Do you know where the drive is mounted ... eg. /media/something ?
If so:
```
sudo chown -R yourname.yourname /media/something
```

chown changes owner, -R means recursive, so that all files & directories below the top level will get updated too, yourname.yourname is a way to set both the owning user and the owning group at the same time (by default you will belong to a group of the same name).

If you don't know where the disk is mounted, run
```
sudo fdisk -l
```
and you should be able to figure out ... post back here if you need some help.

good luck
d

---

### Post by moster on 2009-07-27
After all what I see in this forum, your question is certainly not clutter.

Alternate DaithiF way is this:
```
sudo chmod 777 -R /media/YourDisk
```

---

### Post by MacDuff on 2009-07-27
Thanks DaithiF

I was trying to chown the mount point (/media/usb0) which is where the device was auto-mounting.  It made sense (to me) but did not work.

Your suggestion to find the drive identity using "fdisk -l" put me on track.  I changed the chown command to refer to "dev/sdb1" and it worked when I restarted the computer.

Sometimes I cannot see the obvious and, sadly,those times are getting more frequent.

Thank you
Mac

---

