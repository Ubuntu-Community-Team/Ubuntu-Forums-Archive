---
title: "rsync upper case/ lower case problem!!! HELP!"
date: 2006-06-25
forum: General Help
---

### Post by boom2k1 on 2006-06-25
I use rsync -urv /a /b

to transfer files from one partition to another.

THe problem is that the originally directory contains a subdirectory called T2, but as it is copied to b, it changes to t2!
The problem is that any files and subdirectories inside T2 won't get copied to t2!

Does anyone know how to fix this?

Thanks!

---

### Post by mlind on 2006-06-25
does *rsync -avz /a /b* work?

---

### Post by boom2k1 on 2006-06-25
Let me try now, but I think it is a problem with Fat32 system!
Is there anyway to get around this (besides using Ext3)?

Thanks!

---

### Post by boom2k1 on 2006-06-25
No.. same problem.

Every upper case characters in the filenames got converted into lower case..
hence it gives me such errors.

I don't know if it is only for the Fat32 system.. but I am just trying to find a solution for the Fat32 system!

Any ideas?

Thanks!

---

### Post by mlind on 2006-06-25
This could be related on how your fat32 partition is mounted

---

### Post by mlind on 2006-06-25
see *man mount* and look mount options for vfat

You probably want
shortname=winnt or shortname=win95

---

### Post by boom2k1 on 2006-06-25
Thanks!

How should you mount the drive??

Can you give me the line to do it? Thanks!

---

### Post by boom2k1 on 2006-06-25
There is something REALLY STrange.

On My Fat32 drive,

when I try to make a directory "T2" by creating a folder in the File Browser, it automatically gets rename to "T2"

WHY??

How can I prevent this from happening?

---

### Post by mlind on 2006-06-25
If the fat32 partitions is already mounted, you need to umount it first


For example, your fat32 drive is /dev/hda1 and you want to mount it as /media/storage
```

sudo mount /dev/hda1 /media/storage -t vfat -o iocharset=utf8,umask=000,shortname=winnt

```

try with shortname=win95 too.

---

### Post by boom2k1 on 2006-06-25
OMG PERFECT!!!!!!!!!

THANK YOU SO MUCH!!!


Let me try it with rsync now! I will tell you how it goes !

---

### Post by boom2k1 on 2006-06-25
Perfect.

This would now allow me to do an exact backup!

Thank you for solving my problem!

---

