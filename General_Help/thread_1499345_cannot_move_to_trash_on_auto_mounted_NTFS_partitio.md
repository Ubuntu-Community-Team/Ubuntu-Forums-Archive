---
title: "cannot move to trash on auto mounted NTFS partition?"
date: 2010-06-01
forum: General Help
---

### Post by pythonscript on 2010-06-01
How can I set it so I can move files to trash (not completely delete) on my automatically mounted NTFS partition? It's a shared partition between Windows and Linux, and I don't understand why I can move files to the trash on my external NTFS drives, but not my internal, automatically mounted one. Here's the relevant entry from /etc/fstab:
```

/dev/sda3 /home/user/shared    ntfs    defauls,noatime 0 0

```

/home/user/shared exists, I have sudo rights, etc.

---

### Post by drs305 on 2010-06-01
Try adding this option to the line, "uid=1000", assuming you are the original user. If not, use the "id" command to find your uid number.
> /dev/sda3 /home/user/shared    ntfs    defauls,**uid=1000,**noatime 0 0


This will make you the owner and should create a .Trash-1000 folder where deleted files will be placed. I've not placed a mountpoint where you have but I assume it would work the same way there.

Once you have saved the fstab file, umount and remount the partition.
```

sudo umount /dev/sda3 && sudo mount -a
```

---

### Post by pythonscript on 2010-06-01
That worked flawlessly. Thank you!

---

### Post by dtach on 2010-06-08
Hi, I have a huge problem, I just tried this fix, but accidentally lost my NTFS drives UUID, and now am unable to mount the drive altogether! I am pretty sure I copied the UUID before I replaced it with 1000, but apparently didn't.

HOW DO I FIX IT!? Any help would be amazing, this is probably the worst I've messed up my system, because my desktop is located on the other partition that I don't have access to, I cannot open ANY file or folder with nautilus.

I opened Gparted and got the UUID from there, and posted it back into my fstab with gedit, but it didnt work! and im afraid to shut down just in case it wont boot up again or something...

here is my fstab file contents.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=052a5338-47c3-4224-9120-9c078962c42e	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=116F76BF59B32A05	/media/Storage	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0


/dev/sda1     /mnt/mypartition    ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0

/dev/sda2     /mnt/mypartition    ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0

```


P.S. it is for my drive sd4, the one labelled "storage"

---

### Post by pythonscript on 2010-06-08
Try posting this in a new thread; since I've marked this thread Solved (since *the original post is solved*) a lot of people will pass over it. I would highly recommend starting a new thread with the same description of the problem. Since your post isn't completely related either it's also a good idea. 

You can see the UUIDs of all your partitions by running
```

sudo blkid

```

from the terminal. Its output should set you in the right direction for getting the UUIDs.

---

### Post by dtach on 2010-06-08
you know what, thank you so much! after getting the UUID from gparted, all and pasting it back into fstab, all i had to do was restart... whew. i was just scared of doing that a bit, i freaked out haha, but yeah, thanks for the really quick response, its nice to know that we have some good support here in the forums.

---

### Post by danielpol on 2010-09-27
HI
I had the same problem, could not move files to trash on my ntfs partition. Now this is solved but only partially. I can move files I want tot delete to trash but they do not appear in the Trash from the panel, only in .Trash-1000 folder from the ntfs partition. Anybody knows why ?

---

### Post by JoeloRoss on 2011-01-22
> **drs305 said:**
> Try adding this option to the line, "uid=1000", assuming you are the original user. If not, use the "id" command to find your uid number.



This will make you the owner and should create a .Trash-1000 folder where deleted files will be placed. I've not placed a mountpoint where you have but I assume it would work the same way there.

Once you have saved the fstab file, umount and remount the partition.
```

sudo umount /dev/sda3 && sudo mount -a
```


Excellent !!! adding uid=1000 solved my problem. :D:D:D

---

### Post by ItalOz on 2011-03-13
that was not enough for me to be able to move files to trash.
I had also to add the group id
```
UUID=0A046CF41C7164C6 /media/Data ntfs defauls,uid=1000,**gid=1000**,noatime 0 0
```
because when I was checking the files properties with ls -ls I had that the group was still root, by mounting with the gid as well also the group was at my username.

Note: in my fstab line I use the mounting of the drive by UUID that seems to be more robust than mounting by location like /dev/sda#

hope it helps

---

### Post by micro77 on 2011-10-31
> **drs305 said:**
> Try adding this option to the line, "uid=1000", assuming you are the original user. If not, use the "id" command to find your uid number.



This will make you the owner and should create a .Trash-1000 folder where deleted files will be placed. I've not placed a mountpoint where you have but I assume it would work the same way there.

Once you have saved the fstab file, umount and remount the partition.
```

sudo umount /dev/sda3 && sudo mount -a
```
thank you very mouch...
its works now...
:D

---

### Post by krishnendusarkar on 2011-11-16
> **drs305 said:**
> Try adding this option to the line, "uid=1000", assuming you are the original user. If not, use the "id" command to find your uid number.




thank u very much. that just did it.

---

### Post by oldmankit on 2012-05-02
> **drs305 said:**
> Try adding this option to the line, "uid=1000", assuming you are the original user. If not, use the "id" command to find your uid number.



This will make you the owner and should create a .Trash-1000 folder where deleted files will be placed. I've not placed a mountpoint where you have but I assume it would work the same way there.

Once you have saved the fstab file, umount and remount the partition.
```

sudo umount /dev/sda3 && sudo mount -a
```

Thanks for that, great advice.  It worked a treat for me.

---

### Post by fercsi on 2012-09-26
Hi,

It works only if the system has a single user. What if ours has two users (of course 1000 and 1001), and both would like to use ntfs partitions with trash functionality?

Thanks,
FERcsI

---

### Post by bab1 on 2012-09-26
> **fercsi said:**
> Hi,

It works only if the system has a single user. What if ours has two users (of course 1000 and 1001), and both would like to use ntfs partitions with trash functionality?

Thanks,
FERcsI

NTFS permissions are set when mounting the partition.  You can set a new separate group (gid) at that time.  Add all the users that you want to have access in that group (gid) (i.e ntfsusers or some such name).

---

