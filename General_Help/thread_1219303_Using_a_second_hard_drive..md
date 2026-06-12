---
title: "Using a second hard drive."
date: 2009-07-21
forum: General Help
---

### Post by Sharkface on 2009-07-21
I have ubuntu partitioned on my E drive (along side windows XP), however I also have a C hard drive that I would like to be able to use. I can see everything inside this hard drive, but I have no way of creating, moving, deleting, or editing of any sort. How do I give myself permission, or allow myself, to do so?

---

### Post by Sharkface on 2009-07-21
): Second page already? I would really like to use my other harddrive, beings as it has 100 gigs of free space, while the drive ubuntu is partitioned to only has 10 left.

---

### Post by Bartender on 2009-07-21
Have you downloaded and burned a GParted LiveCD .iso yet?  Over the last few years of experimentation I've come to realize that there are two things I can't do without - a copy of GParted and a few extra HDD's.
Go to GParted website and download the .iso for the latest stable version.
[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

What's on this second drive?
What is it's file system?  NTFS?
Do you want to give Ubuntu the entire second drive?

---

### Post by sefs on 2009-07-21
How I do it is like this....

Say my second hard disk has a fstab as such
```

UUID=d39970dd-5646-4cf4-8190-8880d60bdca2 /mnt/vmware     ext4    relatime      

```

That above tells ubuntu to where to mount my second harddrive.

I have a users group in existance.  I can't remember if I created it manually or it was default in ubuntu.

But I make sure all users of the system are a member of the users group.  Then I run this command.

```

sudo chown -R root:users /mnt/vmware

```

then 

```

gksudo nautilus

```
Then I go into /mnt folder ... right click on the vmware folder and click on properties.  Click on the permissions tab and set the group dropdown box (the one which says users) to full read write access.  I do it that way because i have no idea how to do it via the command line.

so root is owner of the second drive but any user in the users group has free access to read/write to the second drive.

Finally this is the thread that assisted me...
[http://ubuntuforums.org/showthread.php?t=1204155](http://ubuntuforums.org/showthread.php?t=1204155)

---

