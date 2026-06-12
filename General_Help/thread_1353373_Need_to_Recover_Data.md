---
title: "Need to Recover Data"
date: 2009-12-12
forum: General Help
---

### Post by P13808 on 2009-12-12
I'm planning on installing Ubuntu 8.04 on my other computer.  It currently has (compromised) Windows XP Pro.  A virus has crippled it to the point where Windows will not boot past logon.  Because of this, it's impossible to do a safe shutdown.  There's still a lot of valuable files on the hard drive, though, and I need to retrieve them before wiping the drive.  Is there any way to force it to mount or something?

---

### Post by todak on 2009-12-12
Just use a live CD to boot Ubuntu, then mount the XP drive and transfer your needed files to another drive.

---

### Post by harrisonk on 2009-12-12
[SIZE=4]Wait todak, ubuntu will not mount a drive unless it has bin shut down safely.

As for the problem can you shut down Xp from the login page?

If so then you should be able to recover your files.

Hope this helps

Harrisonk
[/SIZE]

---

### Post by serpantman on 2009-12-12
YES! use the force option, its  

 mount -force or  mount -f   <--- one of these

i have used it for the same thing lots of times. :)

---

### Post by harrisonk on 2009-12-12
[SIZE=4]Thanks serpantman, I learned something new.
[/SIZE]

---

### Post by seeker5528 on 2009-12-12
My preference in these types of situations is to use [RIP](http://rip.7bf.de/current/).

In RIP ntfs-3g is kept pretty well up to date and it is often able to do some checking/resetting, then mount the partition without you having to do anything special in situations where the older ntfs-3g would tell you the disk had to be checked and while in an X session RIP provides a menu option to mount/unmount your partitions where you can pick them off a list.

Old or new, if you need it, there is a force option you can use if you mount the partition from the command line:

```
ntfs-3g -o force /dev/whatever /some/mountpoint
```

Later, Seeker

---

