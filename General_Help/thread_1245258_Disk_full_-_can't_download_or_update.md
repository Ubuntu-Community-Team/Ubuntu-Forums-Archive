---
title: "Disk full - can't download or update"
date: 2009-08-20
forum: General Help
---

### Post by robintu on 2009-08-20
I just installed ubuntu 9.04 and got the wireless net working. So I installed wine and was going to download spotify. When I was going to download it, it says there is not enough space in /tmp, and the same goes when I try to update with the update manager.

I booted into live cd hoping I could enlarge the partition used for linux, but I couldn't. So I wonder if I can set it to have temp files on my other partition? I got one unused partition with 300gb or so which could contain a lot.

Can I enlarge the linux partition in some way, or can I make it save stuff to another one?

```
robin@robin-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  216K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  164K  1.5G   1% /dev
tmpfs                 1.5G  480K  1.5G   1% /dev/shm
overflow              1.0M   16K 1008K   2% /tmp
/dev/sr0              699M  699M     0 100% /media/cdrom0
/dev/sda1             281G   37G  244G  14% /media/disk
robin@robin-laptop:~$ 

```

---

### Post by michy99 on 2009-08-20
Read this post which tells how to fix this:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

