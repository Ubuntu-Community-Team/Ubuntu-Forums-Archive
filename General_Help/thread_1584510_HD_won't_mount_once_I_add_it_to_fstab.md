---
title: "HD won't mount once I add it to fstab"
date: 2010-09-29
forum: General Help
---

### Post by searchfgold6789 on 2010-09-29
Hi,
I recently added myself a harddisk with one big ext4 partition on it. I tried to add it to my fstab file like so:
```
UUID=c41b529d-77ee-427c-82b3-dff16f2123a2 /media ext4 rw,user,noexec 0 2
```
But it is not doing what I intended, which was the partition showing up in my Places menu. It also doesn't appear in my /media folder.
Could someone explain to me how to alter the command above so I could have the harddisk open and writable in my Places folder just like my system harddisk?

---

### Post by sisco311 on 2010-09-29
Don't mount it directly in /media, create a new mount point (an empty directory in /media) for the partition.

---

### Post by OrangeMadness on 2010-09-29
The /media doesn't look right. Try creating a subfolder say /media/NewDisk as a mount point.

Also for troubleshooting you can start with the simple:

/dev/sdaX /media/MountPoint ext4 defaults 0 0

See if the partitions appears then in the mount point and start changing your options one by one.

---

### Post by searchfgold6789 on 2010-09-29
Okay, I got it to mount by typing this into fstab instead:
```
UUID=c41b529d-77ee-427c-82b3-dff16f2123a2 /media/sheetmusic ext4 rw,user,noexec 0 2
```
Now it mounts, but you have to be root in order to write to the drive, and it doesn't appear in my Places menu.
I'm going to comment out that line and try to start from the beginning
```
/dev/sdb1 /media/sheetmusic ext4 defaults 0 0
```

---

### Post by sisco311 on 2010-09-29
> **searchfgold6789 said:**
> Okay, I got it to mount by typing this into fstab instead:
```
UUID=c41b529d-77ee-427c-82b3-dff16f2123a2 /media/sheetmusic ext4 rw,user,noexec 0 2
```
Now it mounts, but you have to be root in order to write to the drive


Change the owner of the partition:
```
sudo chown -R $USER: /media/sheetmusic
```

---

### Post by searchfgold6789 on 2010-09-29
Now I will restart thanks :)

---

### Post by searchfgold6789 on 2010-09-29
Well, that command ```
chown
``` you gave me **really **messed up my computer! So I removed the line I added to fstab; now its fixed.
I shall try again.

---

