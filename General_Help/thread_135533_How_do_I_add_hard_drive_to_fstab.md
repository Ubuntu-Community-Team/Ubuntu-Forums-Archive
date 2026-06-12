---
title: "How do I add hard drive to fstab?"
date: 2006-02-24
forum: General Help
---

### Post by ade234uk on 2006-02-24
This question has probably been asked a million times.

1) I have managed to mount my Windows drive and it now appears on the desktop when I enter the following in to shell below. What information should I add to the fstab file so that the drive appears on the next boot up?

mount -t vfat /dev/hdb5 /media/Windows

2) How do I change permissions on this drive so that I can write to the drive. Its letting transfer stuff off the drive, but not letting me stuff back on?

---

### Post by el3ktro on 2006-02-24
If you have a look at /etc/fstab, your fstab line should looks like this:

<device>     <mountpoint>     <filesystem>     <mount options>     0 0

So in your case, it's simply

/dev/hdb5     /media/Windows     vfat     uid=<youruid>,gid=<yourgid>     0 0

Replace <youruid> and <yourgid> with the uid/gid of your user, then all files on the Windows drive belong to you, and you can read/write them. With the mount command you showed here all files belong to root, so you can't write them.

Tom

---

### Post by ade234uk on 2006-02-24
Sorry to bug you even more now. 

How do I find my uid and gid

Replace <youruid> and <yourgid> with the uid/gid of your user

---

### Post by xmastree on 2006-02-24
Do you want everyone to be able to access it?
put it in your fstab like this:
```
/dev/hdb5 /media/Windows vfat umask=000 0 0
```

---

### Post by el3ktro on 2006-02-24
[QUOTE=ade234uk]Sorry to bug you even more now. 

How do I find my uid and gid

Replace <youruid> and <yourgid> with the uid/gid of your user[/QUOTE]

Type 'id' in a Terminal window, this will show you your user's specs. Oh yes, adding a umask option like xmastree proposed is also a good idea. If you want everybody to be able to read your files, add umask=000, if you want only yourself to read the files, add umask=027 or even 077.

Tom

---

