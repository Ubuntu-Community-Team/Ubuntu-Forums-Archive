---
title: "Setting hard drive permissions"
date: 2009-07-10
forum: General Help
---

### Post by lysit on 2009-07-10
Just got a new computer thats replaced an AMD sempron machine, so I've set it up as a old game/file server using ubuntu desktop 9.04. As part of being a fileserver I installed torrentflux which is now fully functioning. However the hard drive I installed ubuntu onto is 8GB (IDE), suffichent to run the OS but leaves about 4GB for files.
To actually store the files I've got 1TB hard drive (Sata) thats mounted itself in /media/storage/ and using nautilus I can read/write files on it. However when I try to use it as the download directory for torrentflux it complains that is isn't chmod 777.
So from /media/ I did:
sudo chmod 777 storage

However this didn't fix the problem, some googling suggested it might be an ownership issue, so I tried:
user@gserve:/media$ sudo chown -hR user:user storage
chown: changing ownership of `storage/untitled folder': Operation not permitted
chown: changing ownership of `storage/new file': Operation not permitted
chown: changing ownership of `storage/down': Operation not permitted
chown: changing ownership of `storage': Operation not permitted

Its at this point I seek help:P

---

### Post by ajgreeny on 2009-07-10
```
sudo chown -hR user:user storage
```You will need the full path of the disk ```
sudo chown -hR user:user /media/storage
```Try that and see if it helps.  What file system is the disk formatted to?  That may make a difference, but I don't think it should.

---

### Post by lysit on 2009-07-10
Same error is given even when specifying the full path.

hard drive is formatted to FAT32 (so if something goes wrong I can pull the data off it on a windows box).

---

### Post by kpkeerthi on 2009-07-10
[https://help.ubuntu.com/community/Fstab#File%20System%20Specific%20Examples]("https://help.ubuntu.com/community/Fstab#File%20System%20Specific%20Examples")

---

### Post by nikhilk on 2009-07-10
> **lysit said:**
> Same error is given even when specifying the full path.

hard drive is formatted to FAT32...

FAT32 has no built-in support for permissions/ACLs etc. It is the Samba system that simulates those things. You might have to make some changes in your /etc/fstab file.
Take a look at the filesystem specific section in manual page for mount. The manpage can be accessed by```
man mount
```

---

