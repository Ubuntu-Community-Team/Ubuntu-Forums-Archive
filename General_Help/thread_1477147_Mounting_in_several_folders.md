---
title: "Mounting in several folders"
date: 2010-05-08
forum: General Help
---

### Post by krippa on 2010-05-08
To get around the limitation of Ubuntu one only allowing synchronization of files in the home folder and not supporting symlinks I am trying to mount my big file store partition in my home folder as well as in the /media/hd folder where it is usually mounted.

So I just copied and pasted the mount line in ```
/etc/fstab
``` and changed the mount folder, run a ```
sudo mount -a
``` and it seemed to be working fine. When I restart Ubuntu however there is a very scary message saying that my hard drive is not working correctly and when I say "cancel" it loads fine but only one mount point is mounted.

Any ideas why that might be? Is there any reason I shouldnt mount a drive in several folders?

Thanks,
Kris

---

### Post by Morbius1 on 2010-05-08
Post the output of the following commands so we can se what's up:

```
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by WorMzy on 2010-05-08
You can only mount a partition once. If you try to mount a partition which is already mounted, you're going to get errors. Instead of mounting it twice, use the bind argument. For example, lets say you want to mount an ntfs partition /dev/sda3 to /media/mystuff and /home/username/Documents; to do this you would put the following into fstab:

```

/dev/sda3      /media/mystuff           ntfs user,exec,rw 0 0
/media/mystuff /home/username/Documents none bind         0 0

```

For all intents and purposes, this creates a duplicate mount point of /dev/sda3, but without actually remounting it.

---

### Post by krippa on 2010-05-08
> **WorMzy said:**
> For all intents and purposes, this creates a duplicate mount point of /dev/sda3, but without actually remounting it.

Thanks a lot! This solves all my problems! Instead of symlinking my music, pictures, videos etc to my home I just added a "binding" for each in my home folder, that way I can synchronize them on Ubuntu One as well!!! :)

I noticed that I dont have to bind the root of the partition with bind, I can also bind subfolders. Here is the result if anyone's interested:

```

UUID=49af66cc-3eab-4d0a-b5a6-e1e18b926b47 /media/hd       ext3    defaults        0       2
/media/hd/Documents /home/kristofer/Documents       none    bind        0       0
/media/hd/Pictures /home/kristofer/Pictures       none    bind        0       0

```

---

### Post by WorMzy on 2010-05-08
Yup, you can bind any folders, whether they're on a mounted partition or on the same partition. But be careful how you move files. For example, I have a similar set up to you, where I have my main storage partition mounted in /media but several folders on that partition bound to my ~/Documents, ~/Videos, ~/Pictures, etc. If, for example I move a video from ~/Videos to ~/Documents, despite the video logically been moved from one folder to another folder on the same partition it will be trying to go through my /home partition too, making the transfer much longer than it needs to be. Instead, if I move the file from /media/Terastore/Videos, to /media/Terastore/Documents, it will be much quicker because it's all been handled by a single partition.

I hope this makes sense.

---

### Post by krippa on 2010-05-08
Yes it does make it more clear. I will think about that when moving stuff around! Thanks!

---

