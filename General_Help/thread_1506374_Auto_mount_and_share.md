---
title: "Auto mount and share"
date: 2010-06-10
forum: General Help
---

### Post by makada on 2010-06-10
Have 2 pcs with xp sp3 only and 1 pc with lucid lynx dual boot with win xp sp3,
The problem:

Have two folders on the desktop in ubuntu pc:
sharedmovies
sharedmusic
The folders are empty

I have two ntfs partitions(internal drive) on this ubuntu pc which i want to share in the windows network so that the other two windows pcs can access (with write support) these two partitions.
The 2 ntfs partitions are /dev/sda5 and /dev/sda6

I mounted /dev/sda5 into sharedmovies and /dev/sda6 into sharedmusic and then changed their sharing options to allow sharing .I edited the /ets/samba/smb.conf file and added
```

[global]
user share owner only = false


```
It worked easily and immediately I could see these two folders in "my network places" with the two ntfs drives mounted on them.

Now I want this mounting and sharing to take place automatically every time i boot into ubuntu. How do I do it? ( Ubuntu knowledge level - very basic but can follow instructions !)

I thought i will make a script using
```

 sudo gedit /home/john/Desktop/scriptToMountAndShare.sh

```

Then i add 
```

sudo mount /dev/sda5 /home/john/Desktop/sharedmovies
sudo mount /dev/sda6 /home/john/Desktop/sharedmusic

```

How to do the sharing thing with script?

To make it executable i run
```

chmod 0755 /home/john/Desktop/scriptToMountAndShare.sh

```
Am i on the right track?
Also I have a username and password for my ubuntu pc, but i have configured it not to ask the password when it boots, I do not want it to ask for password when it mounts or enables sharing on these folders.

---

### Post by makada on 2010-06-10
I think I got it ...(after a lot of Goooglng!)

I just added the lines
```

mount /dev/sda5 /home/john/Desktop/sharedmovies
mount /dev/sda6 /home/john/Desktop/sharedmusic

```

into /etc/init.d/rc.local

Then ran
```

chmod a+x /etc/init.d/rc.local

```

And it was automounting on boot.
As for sharing priveleges, once I had selected to share the folders, ubuntu remebered that.

---

### Post by dino99 on 2010-06-10
mountmanager is an easy way to deal with partitions and devices and their rights

---

### Post by gordintoronto on 2010-06-10
Methinks it would have been easier to create a folder on each of the partitions, then share the folders.

---

### Post by Morbius1 on 2010-06-10
The only problem with your method is that although you have a script that mounts you don't have a script that unmounts. You could run into problems if you shut down before you umnount those partitions.

The classic way to do this would have been to add lines in /etc/fstab that will execute on boot and mount them automatically and unmount them automatically at shut down.
> 
/dev/sda5 /home/john/Desktop/sharedmovies ntfs defaults,nls=utf8,umask=000,uid=1000 0 0
/dev/sda6 /home/john/Desktop/sharedmusic ntfs  defaults,nls=utf8,umask=000,uid=1000 0 0The uid=1000 would have made you the owner and made the "usershare owner only = false" unnecessary.

---

### Post by makada on 2010-06-10
> **Morbius1 said:**
> The only problem with your method is that although you have a script that mounts you don't have a script that unmounts. You could run into problems if you shut down before you umnount those partitions.

The classic way to do this would have been to add lines in /etc/fstab that will execute on boot and mount them automatically and unmount them automatically at shut down.
The uid=1000 would have made you the owner and made the "usershare owner only = false" unnecessary.

Thanks for the tip. Will try your method and post back.

---

