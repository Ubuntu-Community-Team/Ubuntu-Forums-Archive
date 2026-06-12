---
title: "Allowing Apache to RW NTFS mount"
date: 2010-05-13
forum: General Help
---

### Post by play_ on 2010-05-13
Hello.

I keep my site files in an NTFS partition.

When using Ubuntu, Apache gives me a forbidden 403 error when going to [http://localhost](http://localhost)

I had this problem before, and if i remember correctly, to solve it I had to mount the hard drive as root when starting up, so I had this line in fstab:

/dev/sda1       /media/Shared    ntfs-3g    quiet,defaults,locale=en_US.utf8,umask=000     0      0


But having that line there now doesn't make it work. It does mount Shared, and as root, but Apache still gives 403.

Any feedback welcomed :)

---

### Post by KeyserSoze93 on 2010-05-14
Try running:

```

sudo su - nobody

```

This gives you the same privileges that Apache has, and you can see if that allows you to read the drive. If it does, then the problem is with the Apache config.

---

### Post by play_ on 2010-05-14
> **KeyserSoze93 said:**
> Try running:

```

sudo su - nobody

```

This gives you the same privileges that Apache has, and you can see if that allows you to read the drive. If it does, then the problem is with the Apache config.


Thanks for the reply.
Yes i was able to read the drive, and even create a folder in there.

Same thing when used www-data instead of nobody as well.

Also, another fstab line i tried was:
*/dev/sda1       /media/Shared    ntfs-3g    quiet,defaults,nouser,gid=33,uid=1000,locale=en_US.utf8,umask=000     0      0*

(gid 33 being www-data and uid being me)

but that didn't seem to fix it either

---

### Post by play_ on 2010-05-15
Anyone else?

Here's my results of ls -la


**lyrae@localhost:~$** ls -la /media/shared/
drwxrwxrwx 1 root root 12288 2010-05-14 22:25 .
drwxr-xr-x 4 root root  4096 2010-05-15 07:52 ..
drwxrwxrwx 1 root root     0 2010-05-14 01:00 sites
drwxrwxrwx 1 root root  4096 2009-12-02 12:44 stuff


I have also 

su www-data, and was able to read and create directories into /media/shared

So if www-data can access and read the drive, i really have no idea why apache gives permission denied

---

