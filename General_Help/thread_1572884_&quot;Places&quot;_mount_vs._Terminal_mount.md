---
title: "&quot;Places&quot; mount vs. Terminal mount"
date: 2010-09-11
forum: General Help
---

### Post by UncleBoarder on 2010-09-11
How is mounting from the Places menu different than a command line mount?

I have an NTFS volume that can be mounted either way (must be root from command line).  If I mount it from Places, I can delete files/folders and they go to the trash.  But if I mount it from command line..

    sudo mount /dev/sdc1 /media/test

Then (when mounted from command line) if I delete a file/folder it prompts me to skip or discard it immediately.  It doesn't use the .Trash folder.

I want the command line mount to work the same as the Places mount.

---

### Post by akakingess on 2010-09-11
Can you mount it without using "sudo"?

---

### Post by UncleBoarder on 2010-09-12
No, I get an error... "only root can do that".

---

### Post by WorMzy on 2010-09-12
I assume that mounting through nautilus passes a bunch of default arguments to the mount command, but mounting by commandline relies on *you* giving the arguments.

Take a look at /etc/mtab the next time you mount something through Nautilus and see what arguments it was mounted with. Once you know what arguments you should mount the partition with, you can mount it exactly the same way with the mount command.

---

### Post by UncleBoarder on 2010-09-12
That sounds very promising but can you give me a hand with syntax?

Here's the mtab statement when mounted via command line...

   /dev/sdc1 /media/temp fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

And here's the mtab when mounted via Places...

   /dev/sdc1 /media/Backup fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

So apparently I'm missing "default_permissions".

What's the syntax to add default_permissions to my command line mount statement?

---

### Post by WorMzy on 2010-09-12
```
sudo mount -t ntfs-3g /dev/sdc1 /media/temp -o rw,nosuid,nodev,allow_other,default_permissions
```

Should do it. Assuming it's an ntfs partition.

---

### Post by UncleBoarder on 2010-09-12
It does look closer to the Places mount.  Same options when I mount it via command line but interestingly "allow_other" is included twice.  No idea why.

AND... more importantly... it doesn't fix the problem.

When mounted via command line, I can't hit delete to delete a folder.  When I do, I get...

"Cannot move file to trash, do you want to delete immediately?  [Cancel]  [Skip]  [Delete]

But it continues to work properly if mounted via Places.  And now both mount methods show the same mounted options in mtab.

Any ideas?

---

### Post by Miljet on 2010-09-12
I noticed that the two methods are mounting to different mount points, one to /media/temp and the other to /media/Backup. Have you looked at the permissions of those two mount points to see what is different?

---

### Post by WorMzy on 2010-09-12
Maybe it has something to do with the ownership of the files. How does the ls -l output look for the respective directories contents?

(mount the partition one way, open a terminal and "cd" to the folder, then run "ls -l", then unmount the partition, mount it the other way and use "ls -l" again)

If root owns the files, or the file permissions are different for the command line mounted partition, try mounting with this instead:

```
sudo mount -t ntfs-3g /dev/sdc1 /media/temp -o rw,nosuid,nodev,default_permissions,uid=1000,gid=1000,umask=002
```

Assuming that your uid is 1000.

---

### Post by UncleBoarder on 2010-09-13
It works... testing further.

---

### Post by UncleBoarder on 2010-09-14
Yes it was ownership...  Mounted via the Places menu, everything was owned by root.

Your mount statement worked.  I then tried to simplify it and initially ran into some read only problems that I can no longer reproduce.  My first mount would be read only, then if I re-issued the same exact mount command (by using up arrow) the second time it would be read-write.  Strange.

But, as I said, I can't reproduce that.  When I can, I'll post another question.

I'm now using...

sudo mount /dev/sdc1 /media/temp -o uid=1000,gid=1000,umask=002

And it works.  Is my simplified version of WorMzy's solution ok?

Thanks!!!

---

