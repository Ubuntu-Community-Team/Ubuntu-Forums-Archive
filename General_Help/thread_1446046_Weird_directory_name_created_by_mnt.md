---
title: "Weird directory name created by mnt"
date: 2010-04-03
forum: General Help
---

### Post by MaindotC on 2010-04-03
I have this old personal media player - the videg028 - and when I plug it in it has a reference via the command line that I'm not sure how to access.  It appears in mtab as follows:
```
/dev/sdb /media/1 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```
If I list what's in /media it displays it as "?1" but I still can't cd to the directory using "?1":
```

xk@xk:~/Music/march$ ls /media/
?1  b984c0f4-9482-4bb4-90fc-602835d57f4e  cdrom  cdrom0  floppy  floppy0

```
I can still access and use it so my question is not concerning the ability to movie files into and out of it.  My question is what is that character and how would I represent it on the keyboard?  I know I can create an entry for it in fstab but I was just curious about this character if anyone know what it is.  Thanks!

---

### Post by oldfred on 2010-04-03
I just changed the label using Disk Utility on my Tsonic and now it mounts under the label. I had to unmount it to let me change the label but it seemed to work. Mine always can up a 2.0G device or something.

---

### Post by quadproc on 2010-04-03
> **strAlan said:**
> I have this old personal media player - the videg028 - and when I plug it in it has a reference via the command line that I'm not sure how to access.  It appears in mtab as follows:
```
/dev/sdb /media/1 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```If I list what's in /media it displays it as "?1" but I still can't cd to the directory using "?1":

I don't know what that character is but I can suggest how you might find out: use od -x to display the contents of /etc/mtab (or omit the -x if you prefer octal).  If you need to insert an octal special character into a command line then you can escape it with a backslash, as in \021.

quadproc

---

### Post by dcstar on 2010-04-03
> **strAlan said:**
> I have this old personal media player - the videg028 - and when I plug it in it has a reference via the command line that I'm not sure how to access.  It appears in mtab as follows:
```
/dev/sdb /media/1 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```
If I list what's in /media it displays it as "?1" but I still can't cd to the directory using "?1":
```

xk@xk:~/Music/march$ ls /media/
?1  b984c0f4-9482-4bb4-90fc-602835d57f4e  cdrom  cdrom0  floppy  floppy0

```
I can still access and use it so my question is not concerning the ability to movie files into and out of it.  My question is what is that character and how would I represent it on the keyboard?  I know I can create an entry for it in fstab but I was just curious about this character if anyone know what it is.  Thanks!

```
ls -b /media/
```

---

