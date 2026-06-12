---
title: "Trying to mount Documents and Settings"
date: 2009-08-18
forum: General Help
---

### Post by theozzlives on 2009-08-18
Was thinking, a lot of people create a "data" partition in dual boot. I'm thinking there should be a way to access the documents folder in the NTFS partition. I tried the following:

#/My Documents
/sda1/Documents\ and\ Settings	/home/My\ Documents	NTFS	relatime,errors=remount-ro 0       1

any ideas?

---

### Post by geirha on 2009-08-18
The fstab doesn't treat '\ ' as an escaped space, like the shell does. Instead you need to use '\040' to represent spaces in the path.

Though after replacing those spaces with '\040', your approach will still not work. You'll need to add two lines to achieve what you're trying to do. One line that mounts the entire filesystem at some mount point, then mount-binding to mount a directory on another.

```

/dev/sda1 /mnt/windrive ntfs-3g defaults,uid=*yourusername* 0 0
/mnt/windrive/Documents\040and\040Settings /home/*yourusername*/My\040Documents none bind 0 0

```

I'm a bit rusty on which options you should use for ntfs. Check the man-pages for mount and mount.ntfs-3g
```
man mount
mount.ntfs-3g
```

Also, the mount-points will not be automatically created, so you'll need to create those manually. **sudo mkdir /mnt/windrive** and so forth.

---

### Post by mc4man on 2009-08-18
You can't access "My Documents" unless the partition it's on is mounted, so use fstab to mount your xp at boot and make a launcher (( nautilus /path/to/whatever/you/want
Same for vista though it's usually Users -> Username -> Documents

---

### Post by HiImTye on 2009-08-18
yeah, make it easier on yourself. mount the drive, make a symlink (right click > create link). move that symlink wherever.

I removed my 'video' 'documents' 'music' etc folders in my home folder and replaced them with links to my data drive. I figured why have duplicate folders if they're not going to be useful

---

### Post by theozzlives on 2009-08-19
This is just on my test computer, I really have no call for a Windows partition (except for Fax). I was trying to find a way to let others share "Documents and Settings" instead of a separate "Data" partition so I could do a "How To".

EDIT:
So I'm gonna try:

First create folders:
```
sudo mkdir /mnt/windrv
sudo mkdir /home/My\ Documents
```
Then in fstab:
```
/dev/sda1 /mnt/windrv NTFS 0 0
/mnt/windrive/Documents\040and\040Settings /home/My\040Documents none bind 0 0
```

Windows would have to be the biggest partition, whatchya think?
Refer to: [http://ubuntuforums.org/showthread.php?t=1015834]("http://ubuntuforums.org/showthread.php?t=1015834")

---

### Post by geirha on 2009-08-19
Linux in general is case sensitive, so "NTFS" is completely different from "ntfs", and also, the correct driver to use is ntfs-3g. And you really should use 6 fields as the manual states (**man fstab**).
```
/dev/sda1 /mnt/windrv ntfs-3g defaults 0 0
```

Also, do check the manual page for mount.ntfs-3g to see how you can set the proper permissions.

---

### Post by theozzlives on 2009-08-19
> **geirha said:**
> Linux in general is case sensitive, so "NTFS" is completely different from "ntfs", and also, the correct driver to use is ntfs-3g. And you really should use 6 fields as the manual states (**man fstab**).
```
/dev/sda1 /mnt/windrv ntfs-3g defaults 0 0
```

Also, do check the manual page for mount.ntfs-3g to see how you can set the proper permissions.

I figured it out:
[http://ubuntuforums.org/showthread.php?t=1244185]("http://ubuntuforums.org/showthread.php?t=1244185")

---

