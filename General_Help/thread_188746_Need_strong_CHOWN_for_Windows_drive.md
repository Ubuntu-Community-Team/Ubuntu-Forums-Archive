---
title: "Need strong CHOWN for Windows drive"
date: 2006-06-04
forum: General Help
---

### Post by martal on 2006-06-04
I am trying to access, from Ubuntu, a shared folder, a vfat, for Firefox settings, ie cookies.txt, signons.txt, key3.db

Firefox complains.

It's a problem of ownership. I don't how to get the right/full ownership on the shared folder.

After all the chown -R, still it's 755.

What's the trick here?

---

### Post by shrift on 2006-06-04
You cannot chown a windows partition. It does not work. However, try mounting the partition with this as an option "umask=000" That should make it work. If your running the mount command manually it would look something like this: ```
mount -t vfat -o umask=000 /dev/hda2 /media/vfat
```

---

### Post by martal on 2006-06-04
shrift, thanks for that.

my line in /etc/fstab/:
/dev/hda5       /media/hda5     vfat umask=0000,dmask=0000,uid=0002,gid=users,users  0 0

Don't think this is the problem. maybe make a strong chown?

---

### Post by shrift on 2006-06-04
You really shouldn't need all that. I never have trouble with my windows partitions when I use the umask. This is all I do, try making your line look like this:
```
/dev/hda5 /media/hda5 vfat user,umask=000 0 0
```

---

### Post by martal on 2006-06-04
Nope, tried that as you gave.

Drive/Folder permissions are drwxrwxrwx, 1600777

Am I in deep enough?

---

### Post by taurus on 2006-06-04
Tr using
```

umask=0222

```

---

### Post by shrift on 2006-06-04
You cannot chown a windows filesystem. I don't know what this "strong chown" is your talking about, but chown is a command designed to work on linux filesystems. You cannot edit permissions on a windows drive with it. Ubuntu ignores windows permissions on windows drives. Something you DO need to look at though is this; if you do not have permission to the folder on the LINUX filesystem, BEFORE you mount your vfat, you will not have access to it afterwards either.

---

### Post by martal on 2006-06-04
No, didn't work!

Am sure its a chown thing.

Been here before. Really strong chown on all files in the folder, did the job. Can't remember the sytax!

---

### Post by shrift on 2006-06-04
Maybe you are looking for "chmod" That changes file permissions on filesystems. However, that is also a linux only command. You cannot change permission on windows drives with chown or chmod. Unless I am very wrong. I have tried before. Let me know if you figure it out.

---

### Post by MaX on 2006-06-04
[QUOTE=martal]No, didn't work!

Am sure its a chown thing.

Been here before. Really strong chown on all files in the folder, did the job. Can't remember the sytax![/QUOTE]
chown the mount point eg. /media/mydisk so that it's in the disk group
that's the only chown you'll need, other than that it's mounting options.

---

### Post by shrift on 2006-06-04
Indeed MaX! Martal, can you give us the error?

Try mounting it without the fstab somewhere. Try this:
```
sudo mount -t vfat -o umask=000 /dev/hda5 /media/hda5
``` Let me know  if that works.

---

### Post by martal on 2006-06-04
OK. Yep. Will try.

Getting tired now. Going to the pub.

See you tomorrow. :)

---

### Post by mlind on 2006-06-04
[QUOTE=martal]No, didn't work!

Am sure its a chown thing.

Been here before. Really strong chown on all files in the folder, did the job. Can't remember the sytax![/QUOTE]

no man, shrift is right. It's the umask on mount what defines who can access the
files. If it's automounted, then mount magic is on check /etc/fstab.

---

### Post by Horizon on 2006-06-04
[QUOTE=martal]No, didn't work!

Am sure its a chown thing.

Been here before. Really strong chown on all files in the folder, did the job. Can't remember the sytax![/QUOTE]
ROFL lol mate, you just made my day. That's the funniest thing I've heard in weeks, thanks :lol:

---

### Post by givré on 2006-06-04
You should try this option in your fstab
```
defaults,rw,user,auto,gid=100,uid=1000,umask=002,codepage=850
```
uid=1000 will set the owner as you
gid=100 will set the group as your group
umask=002 will set the permissions of the files to 775

---

### Post by martal on 2006-06-04
[QUOTE=Horizon]ROFL lol mate, you just ma
de my day. That's the funniest thing I've heard in weeks, thanks :lol:[/QUOTE]

Why is that so funny?

---

