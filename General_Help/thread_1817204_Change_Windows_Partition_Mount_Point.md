---
title: "Change Windows Partition Mount Point"
date: 2011-08-03
forum: General Help
---

### Post by No1nfoProvided on 2011-08-03
I'm having trouble changing the mount point on my Windows partition. I use "gvfs-mount -d" to mount my partition in Terminal (I believe it's the same as clicking on the "XXXX Filesystem" in nautilus). I don't see anything when regarding /dev/sda2 (device file of the partition) in my fstab. When I mount it by either using gvfs-mount or clicking on it in nautilus, it mounts in "/mount/525CA1975CA175FF". I want to change it to look like something that is not the random numbers. Is this possible?

Also, I was wondering if it was possible to get gvfs-mount -d to work with the exfat filesystem. I can mount by using exfat-fuse, but I like the automounting and the creation of the mount point in the file system by gvfs. I'd rather not be forced to leave an empty folder just for the purpose of mounting.

EDIT: I'm running Lucid 10.04 64-bit

---

### Post by dcstar on 2011-08-03
> **No1nfoProvided said:**
> 
.........
I'd rather not be forced to leave an empty folder just for the purpose of mounting.


Huh, what is the problem with a folder that is taking up NO SPACE on your system?

Just use the way Unix/Linux has provided for decades, it works.

If you want to add a fstab entry correctly, use the **pysdm** package.

---

### Post by Morbius1 on 2011-08-03
That's an interesting use of the "gvfs-mount" command but it has the same default as the Nautilus method. Both methods will use the "LABEL" of the partition as the temporary mount point unless there is no LABEL in which case it uses the UUID number of the partition.

So one way to fix this is to change the label of the partition using gparted. Then it will mount to /media/label-name.

But you need to ask yourself why you are mounting and unmounting this partition. Why not just automount it by adding an entry in fstab. You have actually provided enough information in your post to suggest one:

[1] If the partition is mounted unmount it.

[2] Make a permanent home for your partition to live in - I will use in this example "Data" as the folder name to mount to:
```
sudo mkdir /media/Data
```[COLOR=Blue]*Note: A mount point in /media or in your home directory will automatically place a mount icon on the desktop. If you don't want that then place the mount point anywhere else like /mnt/Data or even /Data.*[/COLOR]

[3] Add the following line to the end of /etc/fstab:
```
UUID=525CA1975CA175FF /media/Data ntfs defaults,uid=1000,umask=000,nls=utf8 0 0
```[COLOR=Blue]*Note: "umask=000" will allow all local users to access that partition. If you want to replicate what a "gvfs-mount" will do then use "umask=077":*
[/COLOR]```
UUID=525CA1975CA175FF /media/Data ntfs defaults,uid=1000,umask=077,nls=utf8 0 0
```[4] Save fstab and run the following command to test for errors and mount the new partition:
```
sudo mount -a
```BTW, **pysdm **cannot reproduce the line in fstab that I recommended above as that utility doesn't know anything about UUID's. As I recall pysdm can't mount by device LABEL either but it's been a while. I installed it once to see what all the fuss was about concerning this utility and removed it once I realized what it did.

---

### Post by No1nfoProvided on 2011-08-03
> **dcstar said:**
> Huh, what is the problem with a folder that is taking up NO SPACE on your system?

Just use the way Unix/Linux has provided for decades, it works.

If you want to add a fstab entry correctly, use the **pysdm** package.

One practical reason is that my /media directory is completely empty. Every time something gets automounted (like a USB stick or my Windows partition), its easier to navigate through the Terminal by just typing "cd /me" then tab twice to navigate through to the thing, instead of having to type that one extra letter. To be perfectly honest, though, I'm probably just a little irked by having 20 different ways to mount things and would like to stick to one system. Just some curiosity on my part too. 

> **Morbius1 said:**
> That's an interesting use of the "gvfs-mount" command but it has the same default as the Nautilus method. Both methods will use the "LABEL" of the partition as the temporary mount point unless there is no LABEL in which case it uses the UUID number of the partition.

So one way to fix this is to change the label of the partition using gparted. Then it will mount to /media/label-name.

But you need to ask yourself why you are mounting and unmounting this partition. Why not just automount it by adding an entry in fstab. You have actually provided enough information in your post to suggest one:

[1] If the partition is mounted unmount it.

[2] Make a permanent home for your partition to live in - I will use in this example "Data" as the folder name to mount to:
```
sudo mkdir /media/Data
```[COLOR=Blue]*Note: A mount point in /media or in your home directory will automatically place a mount icon on the desktop. If you don't want that then place the mount point anywhere else like /mnt/Data or even /Data.*[/COLOR]

[3] Add the following line to the end of /etc/fstab:
```
UUID=525CA1975CA175FF /media/Data ntfs defaults,uid=1000,umask=000,nls=utf8 0 0
```[COLOR=Blue]*Note: "umask=000" will allow all local users to access that partition. If you want to replicate what a "gvfs-mount" will do then use "umask=077":*
[/COLOR]```
UUID=525CA1975CA175FF /media/Data ntfs defaults,uid=1000,umask=077,nls=utf8 0 0
```[4] Save fstab and run the following command to test for errors and mount the new partition:
```
sudo mount -a
```BTW, **pysdm **cannot reproduce the line in fstab that I recommended above as that utility doesn't know anything about UUID's. As I recall pysdm can't mount by device LABEL either but it's been a while. I installed it once to see what all the fuss was about concerning this utility and removed it once I realized what it did.

Thanks. I'll try this out. I don't usually mount and unmount this partition. It's just that when my computer starts up, it isn't mounted. I would still have to run a command or use nautilus to mount the partition, so I was just trying to get the "gvfs-mount" command to work because I don't like making the permanent home thing. A lot of this was just curiosity as well. There are a lot of little quirks about using Linux I find here and there that usually have a "solution," not that it's really a problem.

---

### Post by No1nfoProvided on 2011-08-03
Thanks again Morbius1. I just researched more on partition labels, and it's really easy to change in "System -> Administration -> Disk Utility"

---

