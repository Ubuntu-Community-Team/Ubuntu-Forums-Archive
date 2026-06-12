---
title: "Mount failure - Press S to skip mount or M for manual recovery"
date: 2011-01-16
forum: General Help
---

### Post by romy.mathew on 2011-01-16
Hi 

I saw a post where you were faceing 
"Type s for swith or M or mannual restore"

I got the same message. I tried S but nthing happend then I tried M. it took me to root@ubuntu:/#

How i restore it manunally or if not possible I need to back up the data to pend drive

but i cant find the pendrive in the home section. caould you help me back up the data

---

### Post by romy.mathew on 2011-01-16
Hi when I used sudo vi /etc/fstab it takes me to file shown below

```
# /etc/fstab : static file system information
#
# use blkid -o value -s uuid to print the 
# universally unique idenfifier for a device; # this may be used with UUID= as a more 
# robust way to name device that work even if # disk are added and removed, see fstab(5).

# <file system> <mount point> <type> 
# <options> <dump> <pass> proc

/proc proc nodev,noexec,nosuid 0 0

/host/ubuntu/disks/root.disk / ext4 
loop,errors=remount-ro 0 1

/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
```

I could not able to comment[modify] any line saying readonly file.

---

### Post by CharlesA on 2011-01-16
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

