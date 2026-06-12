---
title: "Permission Denied"
date: 2011-03-25
forum: General Help
---

### Post by jokes_finder on 2011-03-25
Hello all,

   I have a file here that should be executable. I tried to change the permission "Executable" in the permission tab ( after right-clicking on the file ). But just after marking the file as executable, the check mark is removed. I have read some commands using the terminal so I tyed:
```
sudo chmod a+x file_name
```but still not executable

Any help?

Thanks in advance and sorry for my bad English.

---

### Post by ~Plue on 2011-03-25
what type of file is it? and on which file system is the file on?

---

### Post by nice_like_rice on 2011-03-25
Could be on a read-only file system?

Check cat /etc/fstab, I'm not sure how to do that from the GUI.

---

### Post by jokes_finder on 2011-03-25
Type: executable (application/x-executable)

What do you mean by "Which file system"?
I think you mean the folder in File System. If so, it's in subdirectories under /media

---

### Post by jokes_finder on 2011-03-25
It's an ordinary executable file, guys. I can change the permission if it's on the desktop ( I have tried this ).

The file is created; since I'm using NetBeans.

---

### Post by nice_like_rice on 2011-03-25
So to clarify:

You have a file on a different partition, you can't change its permissions. When you move it to the desktop, you can change its permissions, correct?

---

### Post by elliotn on 2011-03-25
cant u right click and go to propeties and enable execution

---

### Post by jokes_finder on 2011-03-25
> **nice_like_rice said:**
> So to clarify:

You have a file on a different partition, you can't change its permissions. When you move it to the desktop, you can change its permissions, correct?

Exactly.
I even tried the follwing command:
```

sudo su
chmod 777 file_name

```
but didn't work too

---

### Post by WorMzy on 2011-03-25
Due to the behaviour you're describing, and the fact that the file is in a folder in /media, I expect that the file in question is on a NTFS or FAT partition which you've mounted. If so, the reason why this is happening is that both NTFS and FAT filesystems do not support UNIX file permissions.

You need to either:

A) copy the file (and any related files needed for execution) to a non-NTFS/FAT filesystem (for example, moving them to your home folder), or
B) follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1604251") to make your NTFS/FAT partition mount with the executable bit already set.

---

### Post by jokes_finder on 2011-03-25
> **elliotn said:**
> cant u right click and go to propeties and enable execution

I did try this. But just after marking the check-box, the check mark is removed.:(
( I have said so in my first main post )

---

### Post by jokes_finder on 2011-03-25
> **WorMzy said:**
> Due to the behaviour you're describing, and the fact that the file is in a folder in /media, I expect that the file in question is on a NTFS or FAT partition which you've mounted. If so, the reason why this is happening is that both NTFS and FAT filesystems do not support UNIX file permissions.


That's new. :)
I'm now very happy to know something new. And yeah, the partition format is NTFS.

I'm reading the tutorial right now. I'll mark this thread as solved if things went smoothly.\

Thanks a lot.=D>

---

### Post by ~Plue on 2011-03-25
you'll need to edit/add the entry to fstab with the exec option

or if its a java file,[FONT=monospace] just run [/FONT]*java -jar /path/to/file.jar*

---

### Post by jokes_finder on 2011-03-25
Sorry, but I can't get what you want to say there.

I have here 6 columns:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
  
```I'll add **0** and **0** in the last two columns.

I'll add **ntfs** in the **file system** column.
**/media/Data** is added in **mount point**

but what should I add in **type** and **options**?

---

### Post by ~Plue on 2011-03-25
> **jokes_finder said:**
> 
I'll add **ntfs** in the **file system** column.

ntfs is the **type**
**file system **is the /dev/sdXx label or the uuid of the drive, run *sudo fdisk -l* or *sudo blkid -c /dev/null *to find it
for the mount point, make sure it exist when the device is unmounted
working options for a normal user are defaults,uid=1000,gid=1000,exec

see [WorMzy]("http://ubuntuforums.org/showthread.php?t=1604251")'s thread for more info

---

### Post by WorMzy on 2011-03-25
> **jokes_finder said:**
> Sorry, but I can't get what you want to say there.

I have here 6 columns:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
  
```I'll add **0** and **0** in the last two columns.

I'll add **ntfs** in the **file system** column.
**/media/Data** is added in **mount point**

but what should I add in **type** and **options**?

Okay, this is going to confuse you, but in this case, "filesystem" doesn't mean filesystem, instead, "type" means filesystem, and "filesystem" means the partition *holding* the filesystem.

So a completed fstab line would look like:

```

# <file system> <mount point>   <type>  <options>                                 <dump>  <pass>
/dev/sda1       /media/Data     ntfs    defaults,auto,uid=1000,gid=1000,umask=002 0       0
```

In the tutorial I linked you to, it shows you how to find the UUID of the NTFS partition, which I recommend that you use instead of "/dev/sdXX".

---

### Post by jokes_finder on 2011-03-25
I have marked this thread as solved. 
Thanks a lot.=D>
Everything is working just fine.
Not only this, but I now the **Data** partition auto mounted ( which is something I wanted since I have Ubuntu installed ).

---

