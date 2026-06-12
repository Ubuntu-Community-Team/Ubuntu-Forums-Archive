---
title: "need help setting permissions on an EXT4 partition"
date: 2010-08-22
forum: General Help
---

### Post by drillerccg on 2010-08-22
Hi, Newbie here.

I have partitioned my external hard drive to 2/3 FAT32 and 1/3 EXT4. The Ext4 partition will not allow me to write (create folder) to it. Someone suggested I use gksu nautilus, go to /media, right click on the partition and change permission to "everyone". The problem is that I see Owner, Group, and Others. All three have a lot of options and "everyone" isn't one of them. Any help is appreciated. Using Lucid.

---

### Post by Earl_Maroon on 2010-08-22
In a terminal try:

```
sudo chown [your username] /path/to/partition
```

That will change the ownership of the partition and should give you full rights.

---

### Post by drillerccg on 2010-08-23
buy would this work if I plug it in a different linux box?

---

### Post by ellgor on 2010-08-23
Hi,

Had a similar issue with a usb pendrive, turned out that an app called "usbmount" was the cause of it, removed said app and everything became normal.

Regards, Ellgor.

---

### Post by drillerccg on 2010-08-23
> **ellgor said:**
> Hi,

Had a similar issue with a usb pendrive, turned out that an app called "usbmount" was the cause of it, removed said app and everything became normal.

Regards, Ellgor.

This is not my problem though. I have wiped everything off of the external hard drive and re-partitioned everything using Gparted.

---

### Post by coolman98 on 2010-08-23
drivemagic might work

---

### Post by mcduck on 2010-08-23
> **drillerccg said:**
> Hi, Newbie here.

I have partitioned my external hard drive to 2/3 FAT32 and 1/3 EXT4. The Ext4 partition will not allow me to write (create folder) to it. Someone suggested I use gksu nautilus, go to /media, right click on the partition and change permission to "everyone". The problem is that I see Owner, Group, and Others. All three have a lot of options and "everyone" isn't one of them. Any help is appreciated. Using Lucid.

In this case "everyone" just means that you have to give full permissions to owner, group *and* others.

Changing the ownership of the drive would also work, and *might* work on other machines as well, depending on the user ID of the user trying to access the drive. The ownership stored on the disk uses UID, not your user name. By default the first created user on Ubuntu is UID 1000, and that's what gets stored as the owner of the drive if you chown it. If the person trying to view the drive on another machine also has UID 1000, the system will consider him the owner.

However if you just ignore who actually *owns* the drive, and instead just change the *permissions* to allow anybody to read & write, you should have no problems accessing the drive as other users or on another computer.

---

### Post by drillerccg on 2010-08-23
> **mcduck said:**
> In this case "everyone" just means that you have to give full permissions to owner, group *and* others.

Changing the ownership of the drive would also work, and *might* work on other machines as well, depending on the user ID of the user trying to access the drive. The ownership stored on the disk uses UID, not your user name. By default the first created user on Ubuntu is UID 1000, and that's what gets stored as the owner of the drive if you chown it. If the person trying to view the drive on another machine also has UID 1000, the system will consider him the owner.

However if you just ignore who actually *owns* the drive, and instead just change the *permissions* to allow anybody to read & write, you should have no problems accessing the drive as other users or on another computer.

so once I gksu nautilus and go to /media and chose the drive, right click and use click permissions, what do I set for those settings? The Owner, groups, and Others all have a bunch of entries I do not recognize. None are everyone or owner. TIA

---

### Post by mcduck on 2010-08-23
For all  "Owner", "Group" and "Others" set the folder permissions to "Create and delete files".

Or just run open a terminal and run "sudo chmod a+rw /media/*yourdrive*" (replacing the "*yourdrive*" with your drive's actual name, of course).

---

