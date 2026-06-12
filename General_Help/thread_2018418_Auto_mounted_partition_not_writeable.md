---
title: "Auto mounted partition not writeable"
date: 2012-07-06
forum: General Help
---

### Post by Macamba on 2012-07-06
Hi,

Trying to auto mount a partition. I entered the following line to my /etc/fstab:
```

UUID=57825d60-616a-480e-bae7-aa1234be /home/macamba/Stuff3	
ext3	defaults        0       2

```

A mount -l gave me:
```

/dev/sdb2 on /home/macamba/Stuff3 type ext3 (rw,commit=0)

```

This is what you would expect, isn't it?

However, when I get the properties of my auto mounted partition the window tells me 
"You are not the owner, so you cannot change the permissions".
Owner, Group are both Root, folder access is greyed out. 

So, what do I need to do to get the mount working?

TIA,
Macamba

---

### Post by Macamba on 2012-07-07
Anyone?

---

### Post by dcstar on 2012-07-07
> **Macamba said:**
> 
.........
So, what do I need to do to get the mount working?


To start with do not mount things inside your /home tree, mount them in /mnt (or any other folder **you** create at root level).

Also, do not mount things in /media as that is a System folder that only the system should use.

If you want to change permissions then do this:
```
gksudo nautilus
```

---

### Post by Morbius1 on 2012-07-07
> **dcstar said:**
> To start with do not mount things inside your /home tree, mount them in /mnt (or any other folder **you** create at root level).

Also, do not mount things in /media as that is a System folder that only the system should use.  
First, none of that about /home, /media, and /mnt is a requirement.

Second, I'm assuming that this is a newly created ext3 partition in which case it's owned by root. There are 100 different ways you can get access to this but one way is simply to take ownership of the mounted partition:
```
sudo chown macamba /home/macamba/Stuff3
```

---

### Post by Bucky Ball on 2012-07-11
> **Morbius1 said:**
> ```
sudo chown macamba /home/macamba/Stuff3
```

Didn't work for me.

---

### Post by dewdrop_world on 2012-07-12
For what it's worth, I'm having the same problem. I can use a secondary fat32 partition (which I use for sharing files with win7 on the rare occasions that I need to use Windows-only software) if I mount it by hand in Nautilus after logging in. But if I edit fstab to have it auto mount during boot, then it's mounted by root and only root can do anything with it.

In Ubuntu 10.04, it was fine.

What has changed about auto-mounting in 12.04?

And is there a way to make it behave in a non-useless way?

---

### Post by techvish81 on 2012-07-13
> **dewdrop_world said:**
> For what it's worth, I'm having the same problem. I can use a secondary fat32 partition (which I use for sharing files with win7 on the rare occasions that I need to use Windows-only software) if I mount it by hand in Nautilus after logging in. But if I edit fstab to have it auto mount during boot, then it's mounted by root and only root can do anything with it.

In Ubuntu 10.04, it was fine.

What has changed about auto-mounting in 12.04?

And is there a way to make it behave in a non-useless way?

start nautilus with gksudo nautilus command in terminal as said above and let the root be owner of the partition , just change the second option of permissions to your username which is in the dropdown list when u click on it , allow read and write access. now the owner is still root but you can read and write on the partition , if that's all you want to do with that partition.

---

### Post by oldfred on 2012-07-13
I hate to comment in a thread with Morbius1 as he understands this and I am just trying to pass along what I have learned mostly from him. :)

I do not recommend FAT32 for any hard drive partition permanently mounted anymore as NTFS supports files over 4GB and has a journal so repair is possible or at least more likely. 

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by dewdrop_world on 2012-07-13
> **oldfred said:**
> 
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Perfect, that's exactly what I needed!

A straight answer to a simple question -- love it.

Thanks so much -- problem solved.

> I do not recommend FAT32 for any hard drive partition permanently mounted anymore as NTFS supports files over 4GB and has a journal so repair is possible or at least more likely.

Ah, OK, will keep that in mind for next time. For this HD, the ship already sailed...

James

---

