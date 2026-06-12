---
title: "Cannot Delete File with Backslash in Filename"
date: 2011-02-06
forum: General Help
---

### Post by LRY on 2011-02-06
Ubuntu 10.04 Guest in VirtualBox

I'm trying to delete a file called

```
springlobby_config\.h
```

I've tried:

```
rm -i *
```

which gives me:

```
rm: cannot remove `springlobby_config\\.h': No such file or directory
```

Tried to rename it:

```
mv * abc
```

which gives me:

```
mv: cannot stat `springlobby_config\\.h': No such file or directory
```

I'm no pro with bash so any help here is appreciated.  I don't think it's a permissions issue because usually the terminal would say permission denied, but perhaps I'm wrong.

---

### Post by b0b138 on 2011-02-06
try rm springlobby_config\\.h

or in quotes  rm "springlobby_config\.h"

---

### Post by LRY on 2011-02-07
> **b0b138 said:**
> try rm springlobby_config\\.h

or in quotes  rm "springlobby_config\.h"

I've tried it.  Gives me the same result as my first post:

```
rm: cannot remove `springlobby_config\\.h': No such file or directory
```

I'm thinking deleting this file might require something more advanced.

---

### Post by wojox on 2011-02-07
Where is this file located?

---

### Post by LRY on 2011-02-07
> **wojox said:**
> Where is this file located?

/media/sf_share/f1/f2/

---

### Post by claracc on 2011-02-07
You go to the directory where there is the file:

cd /media/sf_share/f1/f2/ 

There, I would try : rm springlobby_conf*, if it doesn't work I would try : sudo rm springlobby_conf*

---

### Post by LRY on 2011-02-07
> **claracc said:**
> I would try : rm springlobby_conf*, if it doesn't work I would try : sudo rm springlobby_conf*

It's the same command as the first post.  I just tried it with sudo which results in the same output:

```
rm: cannot remove `springlobby_config\\.h': No such file or directory
```

---

### Post by piquat on 2011-02-07
How about:

```
rm springlobby_config?.h
```?

---

### Post by LRY on 2011-02-07
> **piquat said:**
> How about:

```
rm springlobby_config?.h
```?

Seems like the same command as before.  Tried it and the result is:

```
rm: cannot remove `springlobby_config\\.h': No such file or directory
```

---

### Post by claracc on 2011-02-07
And what about: rm -r springlobby_config\\.h ?

You can read man rm to see the removing options -r or -f or both of them, but you have to be very carefull when use them because you can ruin your system deleting everything.

---

### Post by LRY on 2011-02-07
> **claracc said:**
> And what about: rm -r springlobby_config\\.h ?

-r or -f 

Tried them both in the beginning already...  Even tried:

```
rm * -rf -r -f
```

The -f parameter doesn't have an output but upon listing the directory, I get the similar message:

```
ls: cannot access springlobby_config\.h: No such file or directory
```

---

### Post by slooksterpsv on 2011-02-07
What does:
```

ls -l

```
show?

What kind of partition is it? FAT, EXT*x*, NTFS ?
What happens if you do:

```

sudo rm -r -f ./springlobby_config\\.h

```

In case of permissions issue.

EDIT: WARNING IF YOU TYPE THAT COMMAND IN INCORRECTLY YOU CAN RUIN YOUR SYSTEM AND RUIN YOUR FILES! I TAKE NO RESPONSIBILITY FOR THAT COMMAND!

---

### Post by LRY on 2011-02-07
> **slooksterpsv said:**
> What does:
```

ls -l

```Output:
```
ls: cannot access springlobby_config\.h: No such file or directory
total 0
?????????? ? ? ? ?                ? springlobby_config\.h
```> **slooksterpsv said:**
> What kind of partition is it? FAT, EXT*x*, NTFS ?
Filesystem: ext4
> **slooksterpsv said:**
> What happens if you do:
```

sudo rm -r -f ./springlobby_config\\.h

```
As previously posted, -f parameter has no output, but listing dir gives the output above.  And why would that command be dangerous?  It only applies to the current dir even if it has sudo privileges.  I'm starting to think I might have to boot into some special mode or something...

---

### Post by slooksterpsv on 2011-02-07
No wonder, it looks like its a corrupt file, or corrupt inode on the ext4 partition. Cause it doesn't show any permissions, file size, etc. So it may be a fsck on the partition.

Cause I can create a file called, that same name:

```

-rw-r--r--   1 <user> <group>       5 2011-02-07 01:45 springlobby_config\.h

```

So it's a filesystem corruption.

---

### Post by LRY on 2011-02-07
> **slooksterpsv said:**
> No wonder, it looks like its a corrupt file, or corrupt inode on the ext4 partition. Cause it doesn't show any permissions, file size, etc. So it may be a fsck on the partition.

Cause I can create a file called, that same name:
```

-rw-r--r--   1 <user> <group>       5 2011-02-07 01:45 springlobby_config\.h

```
So it's a filesystem corruption.

I see now; it does seem like filesystem corruption. Good catch.

The system is a guest OS in VirtualBox and the problem file is actually located on the host Windows NTFS partition.  The folder containing the file is mounted in Ubuntu as part of the shared folder component in VirtualBox.  How should I approach to solve this corruption/delete this file?

---

### Post by sydbat on 2011-02-07
> **LRY said:**
> I see now; it does seem like filesystem corruption. Good catch.

The system is a guest OS in VirtualBox and the problem file is actually located on the host Windows NTFS partition.  The folder containing the file is mounted in Ubuntu as part of the shared folder component in VirtualBox.  How should I approach to solve this corruption/delete this file?I believe you will have to delete it in Windows.

---

### Post by LRY on 2011-02-07
> **sydbat said:**
> I believe you will have to delete it in Windows.

Haha, if I could do that, I would have done so a long time ago.  Trying to delete it in the CMD shell gives:

```
The system cannot find the path specified.
```

I would think that Ubuntu would have more control and the ability to delete this file.  Any suggestions?

---

### Post by sydbat on 2011-02-07
> **LRY said:**
> Haha, if I could do that, I would have done so a long time ago.  Trying to delete it in the CMD shell gives:

```
The system cannot find the path specified.
```

I would think that Ubuntu would have more control and the ability to delete this file.  Any suggestions?Can you navigate to the file itself? If not, you may have already deleted it.

---

### Post by oleink on 2011-02-07
> **LRY said:**
> Haha, if I could do that, I would have done so a long time ago.  Trying to delete it in the CMD shell gives:

```
The system cannot find the path specified.
```

I would think that Ubuntu would have more control and the ability to delete this file.  Any suggestions?

have you had any luck changing the file name?

---

### Post by slooksterpsv on 2011-02-07
> **LRY said:**
> I see now; it does seem like filesystem corruption. Good catch.

The system is a guest OS in VirtualBox and the problem file is actually located on the host Windows NTFS partition.  The folder containing the file is mounted in Ubuntu as part of the shared folder component in VirtualBox.  How should I approach to solve this corruption/delete this file?

Just to make sure I understand:
Ubuntu is the guest OS; Ubuntu accesses a Shared Folder where the file is at, which is on an NTFS volume. Correct?

If so, then I would run a chkdsk on the NTFS volume (tell Windows to run one).

If the Volume is NFS, I'm not sure on that one.

---

### Post by LRY on 2011-02-07
> **sydbat said:**
> Can you navigate to the file itself? If not, you may have already deleted it.
We know from the rm and ls messages that something is still there.  Listing the directory in both Windows and Ubuntu shows the file exists.  The file doesn't show in nautilus, but does show in Windows Explorer.

> **oleink said:**
> have you had any luck changing the file name?
Read the first post.

> **slooksterpsv said:**
> Just to make sure I understand:
Ubuntu is the guest OS; Ubuntu accesses a Shared Folder where the file is at, which is on an NTFS volume. Correct?

If so, then I would run a chkdsk on the NTFS volume (tell Windows to run one).

If the Volume is NFS, I'm not sure on that one.
Correct.  NTFS volume, so I'll try running chkdsk; hopefully it would solve the problem.  One thing to note, the file was created in Ubuntu from a makefile I believe.  If you guys have any other ideas, that would be great.

---

### Post by oleink on 2011-02-07
> **LRY said:**
> We know from the rm and ls messages that something is still there.  Listing the directory in both Windows and Ubuntu shows the file exists.  The file doesn't show in nautilus, but does show in Windows Explorer.


Read the first post.


Correct.  NTFS volume, so I'll try running chkdsk; hopefully it would solve the problem.  One thing to note, the file was created in Ubuntu from a makefile I believe.  If you guys have any other ideas, that would be great.

Sorry I was mostly skimming through and didn't fully read it. (I was skimming the responses so far)

---

### Post by oleink on 2011-02-07
> **slooksterpsv said:**
> Just to make sure I understand:
Ubuntu is the guest OS; Ubuntu accesses a Shared Folder where the file is at, which is on an NTFS volume. Correct?

If so, then I would run a chkdsk on the NTFS volume (tell Windows to run one).

If the Volume is NFS, I'm not sure on that one.

'Nother quick suggestion based on this:

try using a bootable version of linux and boot from the disk.  Try to remove it that way (outside the system vs inside)

---

### Post by glene77is on 2011-02-07
Oleink,
In Ubuntu, in one of my user subdir, 
I had a file which showed a locked emblem, 
root permissions, 
and a peculiar filename.  
Finally I was able to delete it using PCMAN file mgr.
Maybe I changed the permissions, 
or was able to rename it before deleting it. 

Don't ask me what else I was doing.  
I had tried everything, just like you are going through.

---

