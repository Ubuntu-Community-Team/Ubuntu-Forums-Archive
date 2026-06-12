---
title: "Configure fstab to change ownership to specific user"
date: 2011-11-14
forum: General Help
---

### Post by pawan613 on 2011-11-14
Haylo all,
I want to mount my NTFS partition with 'dbs' (user) as owner to mount point and all files inside the mount.
I tried changing permissions first on the mount point directories, for e.g., /media/Data using:

sudo chown dbs /media/Data

and it did change the ownership, but after mounting, the ownership was changed to root.

My fstab entry looks like:

/dev/sda2 /media/Data ntfs rw,auto,dbs,sync 0 0

I want to mount /dev/sda2 at /media/Data with owner as 'dbs' and permission as 777 on every file and folder.
Please help me on this and keep it simple.

---

### Post by Cyclane on 2011-11-14
[http://opensuse.swerdna.org/susentfs.html](http://opensuse.swerdna.org/susentfs.html)
> /dev/sdb1    /path_to/mount_point    ntfs-3g    uid=suzette,gid=users,umask=0022    0 0


The source mentions open suse, but fstab is kin of a global linux thing so you can safely use this information. use uid, to set the userid and gid to set the groupid, after that use umask to set the permissions on the mounting point. (umask is the complete opposite of standard permissions. (calculate by performing 7777-'desired permission'=umask)

Also NTFS doesn't use the permissions that linux uses with ext[1-4]. By using the above you will set the permissions on the mounting point itself not the files in teh NTFS filesystem.

---

### Post by Morbius1 on 2011-11-14
> I want to mount /dev/sda2 at /media/Data with owner as 'dbs' and permission as 777 on every file and folder.```
/dev/sda2 /media/Data ntfs defaults,uid=dbs,umask=000,windows_names 0 0
```[COLOR=Blue]Note: The preferred way these days to specify the physical device is not by using the old /dev/sda2 type of format but by using UUID's. To find the UUID for your partition run the following command:[/COLOR]
```
sudo blkid -c /dev/null
```Using the information from the above command the fstab line would look something like this:
```
UUID=DA9056C19056A3B3 /media/Data ntfs defaults,uid=dbs,umask=000,windows_names 0 0
```In any event when you are done editing the line in fstab unmount the partition:
```
sudo umount /media/Data
```Then run the following command which will test for errors and if there are none mount the partition with the new settings - it saves you a reboot:
```
sudo mount -a
```

[COLOR=Blue]**EDIT:**[/COLOR] It's really not necessary to use the "uid=000" option in the fstab line as "defaults" already sets it to that but I like to set it that way explicitly so that there is no confusion as to what I've done.

---

### Post by pawan613 on 2011-11-14
Thank you Cyclane, your post did help me understanding fstab.

---

### Post by pawan613 on 2011-11-14
Thanks a ton Morbius1, it's working exactly how I wanted.
Again thanks a ton for clear reply.

---

