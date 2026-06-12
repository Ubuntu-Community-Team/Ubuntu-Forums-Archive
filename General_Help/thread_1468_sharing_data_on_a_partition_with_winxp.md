---
title: "sharing data on a partition with winxp"
date: 2004-10-21
forum: General Help
---

### Post by bwanakalulu on 2004-10-21
hello !
I am an absolute beginner with linux ! as a matter of fact, I've never experienced anything to do with linux ,but I have decided to use ubuntu on my new laptop cause I like the philosophy behind the whole thing.
I need winxp installed  which I need 4 CAD and GIS programms. I partitioned my HD into three partitions.
one for  win xp, one for ubuntu, and one where I'd like to store my data.
( .docs, tables, music ecc..)
so far so good, win xp works , ubuntu works ( I love it allready!), but I cannot access the data partition from ubuntu..
I would very much appreciate some help


FRIENDSHIP
bwk

---

### Post by elwis on 2004-10-21
It's all about what filesystem you use on the "sharing partition".

For example, if it's FAT32 you should modify your /etc/fstab to mount it at boot-time and specify the filetype as "vfat".

Something like
"/dev/hda3  /mnt/share auto,users,gid=002,umask=002   0  0"

or whatever you prefer..

---

### Post by Mikelevel on 2004-10-21
Modify your fstab

Look your win partitions dev...

```
cfdisk
``` 

quit and remember win partitions dev identificator

```
sudo nano -w /etc/fstab
```

and include win lines... (two examples with ntfs and fat32)

/dev/hdb2       /mnt/win        ntfs    user,auto,noatime,umask=000 0 0
/dev/hdb5       /mnt/win2       vfat    user,auto,noatime,umask=000 0 0

Then quit pressing F2 and save changes 

Remember make win dirs in linux.... (For example..)

```
sudo mkdir /mnt/win 
```

Then reboot your machine

---

### Post by montgomj on 2004-10-21
You don't real;ly have to reboot...

sudo mount /mnt/win   after you make the changes

or even 

sudo mount 

will show how fstab is being "read"

but be sure to have made the mount point before you try to mount the partition.

montgomj

---

### Post by bwanakalulu on 2004-10-22
thanx a lot !

It took me some time and a few cups of coffee to get it right, but at the end I succeeded.
there are a lot of things 4 me to learn and get aquainted with, its really challenging .


have a nice day
bwk

---

