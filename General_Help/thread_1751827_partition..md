---
title: "partition."
date: 2011-05-07
forum: General Help
---

### Post by dondecap on 2011-05-07
hi, I have set a second partition on my 160gig drive, it has been formatted to ext3, and mounted but I cannot use it???
when I try to copy a folder or picture ther it come up with a messege to say I do not have permission............. when I go to properties it says permissions cannot be determind.........
what to do???
regards
don

---

### Post by Paddy Landau on 2011-05-07
Most likely your mount command is not giving permission.

How are you mounting the partition?

Incidentally, why ext3 and not ext4?

---

### Post by dondecap on 2011-05-07
hi mate,
I didn't realise there would be much difference between 3 and 4  I can reformat to 4 .
 I mount it by just click in my computerthere is no 'flag' I was not sure what to use so took a chance and selected none.
right click and select mount does the same problem.
regards
don

---

### Post by WorMzy on 2011-05-07
If you've just created it, chances are it's owned by root. Run
```
sudo chown $USER:$USER /media/mountpoint
```
to change the ownership to your user.

IMPORTANT NOTE: Don't run this command on any other folder, if you change the ownership of a folder which must be owned by root to your user, you can may break your entire system.

---

### Post by dondecap on 2011-05-07
hi  mate,
tried that in terminal.......it comes back with .........
..chown: cannot access `/media/mountpoint': No such file or directory
don@don-OEM ~ $ 
regards
don

---

### Post by Foxcow on 2011-05-07
> **WorMzy said:**
> If you've just created it, chances are it's owned by root. Run
```
sudo chown $USER:$USER /media/mountpoint
```
to change the ownership to your user.

IMPORTANT NOTE: Don't run this command on any other folder, if you change the ownership of a folder which must be owned by root to your user, you can may break your entire system.

Would this work for a fresh install as well?  I have /home on a separate partition but my data is no longer in the new home folder.

---

### Post by dondecap on 2011-05-07
hi mate,
ok well got it now,
I had labled the partition 'STORE' so added that to the command and presto!!
as in 
sudo chown $USER:$USER /media/store
now in properties there is still no permissions but I can use the drive.
many thanks.
regards
don

---

### Post by WorMzy on 2011-05-07
> **dondecap said:**
> hi  mate,
tried that in terminal.......it comes back with .........
..chown: cannot access `/media/mountpoint': No such file or directory
don@don-OEM ~ $ 
regards
don

That's because your partition probably isn't mounted at "/media/mountpoint". You're supposed to replace that part of the command with the actual mount point. e.g. if the partition is mounted to /media/storage, run
```
sudo chown $USER:$USER /media/storage
```

EDIT: Looks like you got it. I don't understand what you mean by "there is still no permissions" though, can you elaborate on that, please?

> Would this work for a fresh install as well? I have /home on a separate partition but my data is no longer in the new home folder.

chown won't help you recover lost files. Rather than derailing this thread, create a new topic about your problem and include all the details you think are relevant. If you've already created a topic, PM me a link to it and I'll take a look.

---

### Post by dondecap on 2011-05-07
hi,
when I go to properties it still says ....
the permisitions of "160 hard disk store" could not be determined.
but I have access and can make folders there.
regards
don

---

### Post by oldfred on 2011-05-07
You also need to set permissions.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed - all underlying folders, do NOT run on non data partitions.
$ sudo chmod -R 777 /media/storage

You may want to permanently mount if you want on reboot:

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by dondecap on 2011-05-08
HI,
many thanks I will try a few of those options, but for now it mounts ok when needed and I can write to the volume.
I can't see where to label this thread as solved so added it to the title
regards
don

---

### Post by Paddy Landau on 2011-05-09
> **dondecap said:**
> I can't see where to label this thread as solved so added it to the title
[How to mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

