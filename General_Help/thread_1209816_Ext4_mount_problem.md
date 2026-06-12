---
title: "Ext4 mount problem"
date: 2009-07-10
forum: General Help
---

### Post by dantata on 2009-07-10
Hey,

I've been trying to mount an EXT4 partition. I don't want its permissions to be root.root, but <user>.<user>. I tried setting gid and uid in fstab, but it won't work for some reason.

Any help would be appreciated.

Cheers.

---

### Post by merlinus on 2009-07-10
Something like this in fstab should work:

/dev/sda1 /data ext4 relatime 0 1

Obviously, change the partition number and mountpoint.

---

### Post by Freezing on 2009-07-10
I have something similar 
Its on my drive where i have windows install (i dont use windows anymore just have some files there)
before it used to work now i get an error
(i thought that it might be the problem that i tryed to re-install the windows and i didnt finish the installation because it said that the cd was not in good condition but that shouldnt be a problem i mean shouldnt it still be abilt read the files that are on the HHD or maybe that is the problem)

Thanks

---

### Post by dantata on 2009-07-10
I actually fixed the problem by chowning a bunch of files - /dev/sd#, the mount point and all files in it and it is now working. Strange ;) Thanks anyway.

---

### Post by daty on 2010-01-06
Hi there

I'd like to do exactly what dantata describes in his/her first post. However, changing the owner/group of the appropriate /dev/sda# does not change the owner/group of the mount point. Maybe because I am using straight Ubuntu?

Is there another way of setting the owner/group to <user>:<user> of my ext4-partition?

Thanks for any hints.

---

### Post by warfacegod on 2010-01-06
Greetings folks, this is what you want:


```
sudo chown -R warfacegod:warfacegod /media/drive name
```



Obviously replace my name with yours and drive name with whatever ubuntu calls your  drive. You'll find the name in the /media folder.

---

### Post by warfacegod on 2010-01-06
Freezing:

Your 1st screen shot tells me that you need to plug your drive into a windows machine and then tell windows to "remove drive safely". Basically, your drive got marked by windows as "THIS IS MINE, YOU CAN'T TOUCH IT, IT'S ALL MINE, GIMME GIMME, BEGONE!

There are other ways to fix that but I gave you the easiest.

---

### Post by daty on 2010-01-07
Thanks warfacegod, but all permissions and ownerships of the contents of the disk are set correctly.

As I said, it is an ext4 partition, which Windows can't even read. (Or do you know a driver which makes it readable in Windows? I would be very glad to know!)

To explain my problem a bit more precisely,  here's a more detailed explanation:
I mount my ext4-drive in fstab  with
 /dev/sda7       /media/data  ext4    auto,users,exec,rw,async        0       2.
/media/data then belongs to root:root, with drwxr-xr-x.
As a consequence, I cannot write to /media/data as a normal user, but in /media/data/example/ I have full rights (as they were given to the example-directory). As this is my data partition I would also like to be able to modify its top level without having to change to root every time.

---

### Post by warfacegod on 2010-01-07
I still suggest using the code I posted.



This might help for Windows:

[http://www.linuxjournal.com/article/9449]("http://www.linuxjournal.com/article/9449")

---

### Post by daty on 2010-01-07
chown daty:daty /media/data did the trick. I hope I don't have to do it after every system reboot...

I'll have a look at the article in a minute.

Thanks, warfacegod.

---

### Post by warfacegod on 2010-01-07
It will stay that way until you change it yourself. Glad to help and I hope the article is what you need.

---

