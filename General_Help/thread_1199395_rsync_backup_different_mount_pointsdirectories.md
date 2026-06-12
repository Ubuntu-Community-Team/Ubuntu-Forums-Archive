---
title: "rsync: backup different mount points/directories?"
date: 2009-06-28
forum: General Help
---

### Post by gravyface on 2009-06-28
Trying to automate backup of the following mounts/directories to a usb drive (/mnt/usbbackup); here's what's in my include file:

+ /home/gravyface/www/*
+ /mnt/data1/music/*
+ /mnt/data1/projects/*

If I run the following, nothing happens, so I checked the man and I'm not specifying a source point (I thought the include-from was the source):
sudo rsync --progress -avz --include-from=/home/gravyface/backup.list /mnt/usbbackup/localbackup/

Tried the following:
sudo rsync --progress -avz --include-from=/home/gravyface/backup.list / /mnt/usbbackup/localbackup/

And it starts backing up the root partition, which is not what I want either.  I'm sure I could specify /mnt/data1/ as my source, but I'm assuming the include-from rules for directories would be relative, and therefore my home directory backup wouldn't work.  What am I doing wrong?
Thanks

---

### Post by unutbu on 2009-06-28
Why not do 
[PHP]
sudo rsync --progress -avz /home/gravyface/www/ /mnt/usbbackup/localbackup/
sudo rsync --progress -avz /mnt/data1/music/ /mnt/usbbackup/localbackup/
sudo rsync --progress -avz /mnt/data1/projects/ /mnt/usbbackup/localbackup/[/PHP]

---

### Post by gravyface on 2009-06-29
Yes, I know I can do that, but that makes it harder to script/maintain; I want to allow others to add directories to the rules file without having to modify the backup script.

---

### Post by unutbu on 2009-06-29
```
#!/bin/bash
while read x; do
    base=$(basename "$x")
    root=$(dirname "$x")
    echo "sudo rsync --progress -avz "$root/$base/" /mnt/usbbackup/localbackup/$base"
done < /home/gravyface/backup.list 

```
with
```
% cat backup.list
/home/gravyface/www
/usr/local/share/applications/
/usr/local/share/icons/hicolor/128x128/apps/

```

yields

```
sudo rsync --progress -avz /home/gravyface/www/ /mnt/usbbackup/localbackup/www
sudo rsync --progress -avz /usr/local/share/applications/ /mnt/usbbackup/localbackup/applications
sudo rsync --progress -avz /usr/local/share/icons/hicolor/128x128/apps/ /mnt/usbbackup/localbackup/apps
```

---

### Post by decoherence on 2009-06-29
I don't think 'include-from' is what you want. I believe the include/exclude statements are for filtering a list of files, not for generating one. Try 'files-from' instead...

---

