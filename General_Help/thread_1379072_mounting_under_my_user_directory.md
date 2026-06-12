---
title: "mounting under my user directory"
date: 2010-01-12
forum: General Help
---

### Post by ocpmture on 2010-01-12
Hi, I want to mount a new partition under a directory inside my home folder.. eg, /home/myname/newdisk

To have it automount, I guess i would put /home/myname/newdisk as mount point inside fstab. My questions is,  Is putting a user's name inside fstab considered hackish/bad? are there better ways to do this?

---

### Post by lotharmat on 2010-01-12
afaik, if you create the directory you plan to mount to; all should be fine!

---

### Post by Bucky Ball on 2010-01-12
It should be fine, but why are you not mounting it in /media with the rest of your partitions?

```
 /media/newdisk
```eg:

```
 mkdir /media/newdisk
```... and then add the appropriate line in fstab. What format is the partition?

You can get the UUID from this command:

```
sudo blkid
```

... then just copy an entry already in fstab and change the details. For ext3 something like:

```
UUID='your UUID number' /path/to/newdisk ext3 relatime 0 2
```

---

### Post by ocpmture on 2010-01-12
I guess i could do that, but I just felt the content is more appropriate inside one of the folders inside my home directory.

---

### Post by arubislander on 2010-01-12
Of course you are free to do as you choose (freedom of choice after all is also what Linux is about) so you could go ahead and mount the device directly under your home folder, but what I've done is make a hidden directory in /home (/home/.media) as I also considered the content should not be accessible under /media, and mounted my drive to there. Then in my home folder I made a symbolic link to /home/.media  I know it's a roundabout way, but it works for me.

---

### Post by oldfred on 2010-01-12
I actually do both. I directly mount my ntfs partition but link my /data partition.

# Entry for /dev/sda2 :
UUID=2A87EC53669130A9                      /home/fred/shared  ntfs-3g      defaults                             0  0  
# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
etc for all standard folders in /home and a few additional folders that I have. Home has almost no data other than the system hidden files/folders.

---

