---
title: "How to automount a second hard drive?"
date: 2012-06-17
forum: General Help
---

### Post by peyre on 2012-06-17
I bought myself an SSD and installed Xubuntu on it, leaving my old mechanical drive in place (but in second place) for bulk storage.  But Xubuntu doesn't automount it, so when I go to play music (one of the first things I do on bootup), it won't play until I go into Places or Thunar and tell it to mount the drive.  Is there a way to get the OS to automatically mount it?  The drive is identified in Thunar as

/media/44864ed9-9a8f-48f3-b024-b3dee0dc3fba

or in GParted as /dev/sdc.

---

### Post by BBQdave on 2012-06-18
Check out

Settings > Removable Drives and Media

Though I think the drive of interest should appear in Thunar, given you are booting from an external drive.

And on a side note, you may want Xfce on your machine's drive for better system response :)

---

### Post by adroitster on 2012-06-18
What is the file system on the external mechanical drive. If it's NTFS then 
"NTFS configuration tool" can help you to configure automount. It should be available in synaptic.

---

### Post by c2tarun on 2012-06-18
you can always write a script to mount your partition and put that script in startup-applications :)

---

### Post by efflandt on 2012-06-18
The OP did not say either drive was external.  External drives (like USB) are usually auto mounted by default, but other internal drives are not, unless an entry is added to /etc/fstab.

/etc/fstab can be edited with **gksu gedit** (or **sudo nano** in terminal or console), but that is best done using its UUID (apparently 44864ed9-9a8f-48f3-b024-b3dee0dc3fba) instead of /dev/sdc.

First you need to create a mount point with **sudo mkdir** (typically /media/whatever_name unless you want to mount it elsewhere), add an entry to /etc/fstab for it (see man fstab), then it should automount when you boot.

Note: For the SSD I boot from I use options in the option field: **noatime,discard,data=ordered,errors=remount-ro** but for a regular drive you would typically just use **errors=remount-ro**.  The numbers at the end would typically be 0 1 for a Linux filesystem or 0 0 for other file systems like ntfs.

One other thing that saves writing small files to the SSD as long as you are not doing something that needs a lot of tmp space, since tmp is cleared on boot, is an fstab entry:
```
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0
```

---

### Post by peyre on 2012-06-19
Thanks everyone!  No, this is my old Xubuntu HD, so it's formatted ext4, as it happens.  It's also not set up as a removable disk--it's connected internally via SATA cable...so it doesn't appear in Removable Drives and Media.

The script idea sounds like a good one, but modifying fstab sounds even better, if I can get the syntax right.  But I-----OH MAN!  MountManager!  Why didn't I think of that?  I'll give that a try; I should be able to tell it to automount the drive on bootup.

---

### Post by peyre on 2012-06-19
Yep, that seems to have worked.  Thanks guys!

---

### Post by peyre on 2012-06-20
Ok, I have the drive mounting automatically now (as /media/Storage), but it's disappeared from Places.  Anyone know how to get it back?

---

### Post by c2tarun on 2012-06-22
> **peyre said:**
> Ok, I have the drive mounting automatically now (as /media/Storage), but it's disappeared from Places. Anyone know how to get it back?
 
 
quick workaround will be, try adding that locaiton as Bookmark :)

---

### Post by peyre on 2012-06-22
> **c2tarun said:**
> quick workaround will be, try adding that locaiton as Bookmark :)

A Bookmark?  What, like in Firefox?

---

### Post by oldfred on 2012-06-22
Where did you mount it. A mount in / or /mnt will not show in places. Mounts directly to /home  or /media should show in places in Nautilus (Ubuntu). Not sure if same for Xubuntu but I would expect so.

I always mount to /mnt/data and then link all the folders back to /home. That way it does not show in Nautilus (with Ubuntu).

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by peyre on 2012-07-11
> **oldfred said:**
> Where did you mount it. A mount in / or /mnt will not show in places. Mounts directly to /home  or /media should show in places in Nautilus (Ubuntu). Not sure if same for Xubuntu but I would expect so.

Sorry for the delay!  I mounted it in /media.

---

