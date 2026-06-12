---
title: "Disk Question"
date: 2010-05-17
forum: General Help
---

### Post by brayden551 on 2010-05-17
Oh  :'(.  I kinda didn't know that once you set your disk size, Theres no changing it. Is there? It keeps warning my about space and I cant figure out what to do? 

~Brayden551

---

### Post by Directive 4 on 2010-05-17
hi,

so have you done a install and messed it up?

---

### Post by brayden551 on 2010-05-17
> **Directive 4 said:**
> hi,

so have you done a install and messed it up?

Well.. I set the storage (drive) too small in wubi. Can I Change it? I cant use VirtualBox and It keeps warning me about low storage!

---

### Post by drs305 on 2010-05-17
brayden551,

Welcome to Ubuntu and the Ubuntu forums.

Well, as I composed my response you provided what we needed to know.

If you are using an Ubuntu install within Windows, changing the size of the install is fairly complex. You can move certain parts of the install to other locations but in general this is probably going to be more trouble than it is worth. Have you spent a lot of time tweaking this install?


Old and no longer relevant:
However, with a normal install, you have various options. You *can* resize an Ubuntu partition while using the LiveCD. 

You may also have just acquired too much trash on your system, have large log files, made a backup to the wrong place, etc.

If you run this command we can see what we are working with:
```
sudo df -Th
```

---

### Post by brayden551 on 2010-05-17
brayden@ubuntu:~$ sudo df -Th
[sudo] password for brayden: 
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/loop0    ext4     17G   16G   57M 100% /
none      devtmpfs    1.5G  372K  1.5G   1% /dev
none         tmpfs    1.5G  2.1M  1.5G   1% /dev/shm
none         tmpfs    1.5G  208K  1.5G   1% /var/run
none         tmpfs    1.5G     0  1.5G   0% /var/lock
none         tmpfs    1.5G     0  1.5G   0% /lib/init/rw
/dev/sda3  fuseblk    286G   64G  223G  23% /host

Thanks for The Welcome and Fast Responce!

[IMG]http://i43.tinypic.com/scwfpv.png[/IMG]

---

