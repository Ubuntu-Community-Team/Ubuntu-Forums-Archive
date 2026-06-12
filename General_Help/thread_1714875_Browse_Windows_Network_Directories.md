---
title: "Browse Windows Network Directories?"
date: 2011-03-26
forum: General Help
---

### Post by Rocket J Squirrel on 2011-03-26
Though File Manager allows me to browse Windows network directories ( Ctrl-L shows a path like smb://diskstation/mikeother/Web/Alta_Vista ), I can't figure out how to browse to them in applications like Firefox, which doesn't show "Network" as an option when doing File > Open. 

How can I browse to the Windows network within FF?

---

### Post by dcstar on 2011-03-26
> **Rocket J Squirrel said:**
> Though File Manager allows me to browse Windows network directories ( Ctrl-L shows a path like smb://diskstation/mikeother/Web/Alta_Vista ), I can't figure out how to browse to them in applications like Firefox, which doesn't show "Network" as an option when doing File > Open. 

How can I browse to the Windows network within FF?

You need to mount the folders using /etc/fstab.

Install the **pysdm **tool and it may allow you to set this up via a GUI.

---

### Post by mikewhatever on 2011-03-26
When you hit Fire->Open, a file browser window opens (which is not Firefox), so if you have the shared folder bookmarked, it will be in that window. To bookmark a folder, open it, then Bookmarks->Add Bookmark.

---

### Post by Rocket J Squirrel on 2011-03-28
Thanks guys -- still not getting it.

Mikewhatever: I don't see how to bookmark a shared, networked folder using the File > Open window if I can't see it to bookmark it. The issue here is that while I can browse to shared folders on our NAS on the Windows network using File Manager, I can't browse to them in such a window as FF's File > Open. 

dcstar: I installed pysdm but can't figure it out. I've looked at online documentation and websites, but have hit a brick wall. Editing fstab looks formidable. 

ADDITIONAL INFO: The shared folders visible in Network Manager seem to be mounted already. If I run:

```
gvfs-mount smb://diskstation/shared_folder
```

I get:
```

Error mounting location: Location is already mounted
```

If that's accurate, then why can't I browse to that folder within FF's File > Open window?

Thanks all for help.

---

### Post by newbuntuxx on 2011-03-28
Try this:

umount the network file share.


Then use this to mount it:
```
mount -t cifs -o username=guest //file.share.ip/dir /local/mount/dir
```

Where:
file.share.ip =x.x.x.x ip address of file share
dir = share name (which is most of the time similar to the shared folder name)
/local/mount/dir = this is the local mount point. Normally in: /media/whatever

Then see if firefox sees it.

---

### Post by Rocket J Squirrel on 2011-03-28
Thank you,

I did this

```
sudo mount -t cifs -o username=Admin,password=mypassword //192.168.1.20/littlemike /media/diskstationlittlemike
```and got this

```
mount: Connection refused
```

---

### Post by newbuntuxx on 2011-03-28
Try:

```
sudo mount -t smbfs -o username=Admin,password=mypassword //192.168.1.20/littlemike /media/diskstationlittlemike

```

If you get the same error, then try:

Try:

```
sudo smbclient -L 192.168.1.20
```
It will ask you for a password, enter the root pass of 192.168.1.20.

See if this lists all your fileshares on machine 192.168.1.20.

---

### Post by JRV on 2011-03-28
Type it into the address box:
```
smb://HOSTNAME/SHARENAME
```

This mounts the share the first time you try to open a file, not a directory.
The second time you click on a file you can open or copy it.
But you can not move or delete it.

After it mounts the share is available in nautilus as normal.

---

### Post by Rocket J Squirrel on 2011-03-28
Thank you.

The smbfs version gave

```
mount: wrong fs type, bad option, bad superblock on //192.168.1.20/littlemike,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
sudo smbclient -L 192.168.1.20
```

gave:

```
Connection to 192.168.1.20 failed (Error NT_STATUS_CONNECTION_REFUSED)
```

dmesg | tail gave
```
[35015.585540] smbfs is deprecated and will be removed from the 2.6.27 kernel. Please migrate to cifs
[35015.585554] smbfs: mount_data version 1919251317 is not supported

```

---

### Post by Rocket J Squirrel on 2011-03-28
```
smb://192.168.1.20/littlemike
bash: smb://192.168.1.20/littlemike: No such file or directory

```

As a point of reference, this is how Network Manager shows the path to the target directory when I mount the target through NM and press Ctrl-L:

smb://diskstation/littlemike/

But 

```
smb://diskstation/littlemike/
bash: smb://diskstation/littlemike: No such file or directory
```

---

### Post by Morbius1 on 2011-03-28
To answer your original question, when Nautilus mounts it uses:
>  gvfs-mount smb://server/shareIt automatically creates a mount point in a very odd location:
> /home/your-user-name/.gvfs/share on serverThe reason Firefox can's see it is because it's in a hidden directory ( .gvfs ). 

To enable Firefox to see it do the File > Open then right click an open space in that windows and select "show hidden files"

---

### Post by Rocket J Squirrel on 2011-03-28
Hey there Morbius1,

It is just as you say. Like magic, FF see the mount. 

I wonder if they could make finding mounted networked drives less transparent?

Many thanks for the help, all!

---

