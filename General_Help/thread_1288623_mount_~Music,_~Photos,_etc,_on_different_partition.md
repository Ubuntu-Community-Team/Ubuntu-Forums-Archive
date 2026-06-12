---
title: "mount ~/Music, ~/Photos, etc, on different partitions"
date: 2009-10-11
forum: General Help
---

### Post by pythonscript on 2009-10-11
Is there any way to mount the subfolders of my home directory on a different partition than the config files? I'd like to have my .*programname* folders/files on one partition, and my folders like ~/Music and ~/Videos on a different one. Is this possible, and if so, how can I work set up this? Thanks!

---

### Post by SuperSonic4 on 2009-10-11
Yes, it is roughly the same as making a new /home. You'll be doing a lot of this as root so it may be better to give yourself a root shell throughout. I'd recommend you are familiar with the terminal

**edit2: Copy only one line at a time. Also do you want your media on separate partitions or as subfolders in one partition?**

```
cd /mnt
sudo mkdir Photos Music Videos
```

Lauch gparted and make the partitions you want
```
gksu gparted
```

Make a note of where the partitions are, I will assume they are sdb1 sdb2 and sdb3 but you can use ```
sudo fdisk -l
```

Now edit fstab as root ```
sudo nano /etc/fstab
```. Add something like where ext4 is the filesystem and sdb1 is the location (as above)

```
/dev/sdb1       /mnt/Photos     ext4    defaults  0 0
/dev/sdb2       /mnt/Music      ext4    defaults  0 0
/dev/sdb3       /mnt/Videos     ext4    defaults  0 0

```

mount all ```
sudo mount -a
```

```
cd
sudo mv -v ~/Photos/* /mnt/Photos
sudo mv -v ~/Music/* /mnt/Music
sudo mv -v ~/Videos/* /mnt/Videos
```

Change the owner to you 
```
sudo chown -Rv username:username /mnt/Photos
sudo chown -Rv username:username /mnt/Music
sudo chown -Rv username:username /mnt/Videos
```

et voila. You can then delete the ones in /home


**EDIT: Changed two steps around**

---

### Post by oldfred on 2009-10-11
If you want to see them in home I think you can edit this hidden file that has entries like this:

/home/fred/.config/user-dirs.dirs

XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/"

---

