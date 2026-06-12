---
title: "2nd HD visible as directory in /home"
date: 2010-09-28
forum: General Help
---

### Post by locutuz on 2010-09-28
I made a media station with XBMC and this is working just fine. Now I have an internal hard disk NTFS formatted loaded with multimedia stuff. I would like to appear the disk as directory in my home. Example: /home/xbmc/multimedia where multimedia redirects to the root of the NTFS disk. Is this possible?

---

### Post by Grenage on 2010-09-28
Yup, you can either mount the disk to that directory, or use a symlink.  I'd use a link like so:

```
ln -s /media/drivex /home/xbmc/multimedia
```

Where /media/driveX is the path to your mount point.

---

### Post by locutuz on 2010-09-28
Thanks for your fast reply. I will try this right away this evening. This way I can share the multimadia directory with samba?

Oh, by the way: If I install the NTFS disk I assume it will be mounted automatically. As XBMC doesn't have a desktop like (k)ubuntu, how do I get the diskpath info as /media/drivex in your example?

---

### Post by Grenage on 2010-09-28
Sharing shouldn't be a problem, it's easy via the Gnome GUI, but not a chore via command line.  You'll need command line access or a GUI like gnome to locate the drive and add a symlink.  While I use XBMC at home, I run it on top of Gnome, rather than as the desktop itself (autostart at load).

---

### Post by locutuz on 2010-09-28
I try to keep my XBMC box as clean as possible. Am I right to do 
```
sudo fdisk -l
```
via ssh to show the mounted disks?

---

### Post by Grenage on 2010-09-28
Yup, that will list any discs plugged in and detected.

---

### Post by srs5694 on 2010-09-28
I'm pretty sure that the disk will only be automounted *after* you log in. I'm not positive if automounted disks are unmounted when you log out. In any event, if you intend to share the files via Samba (which runs whether or not you're logged in), relying on the GNOME automounter is a bad idea. Thus, I recommend creating an /etc/fstab entry to directly mount the partition at /home/xbmc/multimedia rather than using the symbolic link and relying on the automounter. The entry would look something like this:

```

/dev/sdb5      /home/xbmc/multimedia     ntfs-3g   uid=1000  0 0

```

You must change /dev/sdb5 to the appropriate partition identifier, or use a LABEL= or UUID= option instead. (Use blkid to find the UUID values for your partitions). The /home/xbmc/multimedia directory must exist. You can adjust the options (uid=1000 in this case) as you see fit (type "man ntfs-3g" to learn about NTFS-3g options).

---

### Post by locutuz on 2010-09-30
Thanks srs5694 and Grenage,

Especially the last post helped me a lot. I have now exactly what I wanted!

Thumbs up!

---

