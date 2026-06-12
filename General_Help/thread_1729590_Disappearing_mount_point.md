---
title: "Disappearing mount point"
date: 2011-04-15
forum: General Help
---

### Post by james25182 on 2011-04-15
I've just formatted a new USB drive to ext4. After creating a mountpoint (/media/Vids) and mounting it I changed permissions so my user owned the filesystem. I added the filesystem to /etc/fstab. 

However, when unmounting the drive the mountpoint directory disappeared and I have to manually recreate the mountpoint everytime I want to remount the drive. What's going on?

Thanks in advance!

James

---

### Post by ajgreeny on 2011-04-15
What commands did you use to change the permissions of the mount point?

---

### Post by james25182 on 2011-04-15
I did:

[FONT="Courier New"]sudo chown james:james /media/Vids[/FONT]

Permissions are set at [FONT="Courier New"]drwxr-xr-x[/FONT] as default. I didn't change them.

---

### Post by ajgreeny on 2011-04-15
And you used ```
sudo mkdir /media/Vids
``` to make the mountpoint folder?

If so, I can not figure out why the folder disappears after unmounting.  It sounds as if you are letting the system make the folder each time you attach the disk, having given that USB disk a label of Vids.  That would mean that it mounts automatically each time at /media/Vids, but the folder would be new, and as it is ext4, it would belong to the root filesystem again.

I use an ext3 formatted USB disk for the backups of my system, and that works without fault for me, the folder in /media being owned my me, not root.  I also have permanent folders on the USB disk, one for me, another for my wife, both of which are owned by me.  Try making a folder on your disk and giving yourself ownership of that folder as well as the mountpoint.

---

### Post by tredegar on 2011-04-15
The mountpoint gets the permissions of the disk when the disk is mounted.
This should fix it for you:
```
sudo -i
mkdir /media/vids
mount /dev/whatever /media/vids
chown root:root /media/vids
chmod 777 /media/vids
umount /media/vids
nano /etc/fstab
*Make a line for the device*
UUID=04450b5a-a6ef-479d-98b5-cbfc4667861b  /media/vids  ext4 defaults 0 2
*Save the file*
mount -a
exit
```
You can get _your_ disk's UUID by plugging it in and then doing **sudo blkid**. I am suggesting you use mount-by-UUID as the **/dev/whatever** may change if you have other devices plugged in.

The above makes root the owner of the drive, but anyone can read / write it. This means that it is sharable between users, who might not want others messing with their files (they just set the perms for their files to be rwx------ for them to become unreadable and unwriteable by others)

---

